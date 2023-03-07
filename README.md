import pygame
import sys

# Set up the game window
pygame.init()
screen = pygame.display.set_mode((800, 600))

# Create the player character
player_image = pygame.image.load("player.png")
player_rect = player_image.get_rect()
player_rect.center = (400, 300)

# Create the treasure
treasure_image = pygame.image.load("treasure.png")
treasure_rect = treasure_image.get_rect()
treasure_rect.center = (700, 500)

# Create the game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
    
    # Move the player character
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        player_rect.move_ip(-5, 0)
    if keys[pygame.K_RIGHT]:
        player_rect.move_ip(5, 0)
    if keys[pygame.K_UP]:
        player_rect.move_ip(0, -5)
    if keys[pygame.K_DOWN]:
        player_rect.move_ip(0, 5)
    
    # Check for collisions with treasure
    if player_rect.colliderect(treasure_rect):
        print("You found the treasure!")
    
    # Draw the game objects
    screen.fill((0, 0, 0))
    screen.blit(player_image, player_rect)
    screen.blit(treasure_image, treasure_rect)
    
    # Update the display
    pygame.display.update()
