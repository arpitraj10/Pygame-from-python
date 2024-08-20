# Pygame-from-python
import pygame
import sys

# Initialize Pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Bouncing Ball Simulation")

# Colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)

# Ball properties
ball_radius = 20
ball_color = WHITE
ball_pos = [WIDTH // 2, HEIGHT // 2]
ball_vel = [5, 3]  # Velocity in x and y directions

# Main loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Update ball position
    ball_pos[0] += ball_vel[0]
    ball_pos[1] += ball_vel[1]

    # Check for collisions with the walls and bounce
    if ball_pos[0] - ball_radius <= 0 or ball_pos[0] + ball_radius >= WIDTH:
        ball_vel[0] = -ball_vel[0]
    if ball_pos[1] - ball_radius <= 0 or ball_pos[1] + ball_radius >= HEIGHT:
        ball_vel[1] = -ball_vel[1]

    # Drawing
    screen.fill(BLACK)
    pygame.draw.circle(screen, ball_color, ball_pos, ball_radius)

    pygame.display.flip()
    pygame.time.Clock().tick(60)

pygame.quit()
sys.exit()
