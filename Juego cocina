import pygame
import sys

pygame.init()

width = 800
height = 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Juego de cocina")

WHITE = (255, 255, 255)
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 255)
gray_light = (200, 200, 200)
gray_dark = (50, 50, 50)
purple_pastel = (150, 130, 255)
pink_pastel = (255, 150, 180)

background_image = pygame.image.load("cocina.png")
background_image = pygame.transform.scale(background_image, (width, height))

chef_image = pygame.image.load("kitty chef.png")
chef_image = pygame.transform.scale(chef_image, (100, 100))
chef_rect = chef_image.get_rect(center=(width // 2, height // 2))

play_button = pygame.image.load("play_button.png")
play_button = pygame.transform.scale(play_button, (100, 100))
play_button_rect = play_button.get_rect(center=(width // 2, height // 2))

font = pygame.font.SysFont(None, 30)

text = font.render("Juego de cocina", True, WHITE)
text_rect = text.get_rect(center=(width // 2, height // 2))

ingredient_images = {
    "Pan": pygame.transform.scale(pygame.image.load("Pan.jpg"), (100, 100)),
    "lechuga": pygame.transform.scale(pygame.image.load("lechuga.png"), (100, 100)),
    "tomate": pygame.transform.scale(pygame.image.load("tomate.jpg"), (100, 100)),
    "Queso": pygame.transform.scale(pygame.image.load("Queso.jpg"), (100, 100)),
    "jamon": pygame.transform.scale(pygame.image.load("jamon.jpg"), (100, 100)),
    "segundo pan": pygame.transform.scale(pygame.image.load("segundo pan.png"), (100, 100))
}

ingredient_positions = {
    "Pan": (50, 50),
    "lechuga": (200, 50),
    "tomate": (350, 50),
    "Queso": (500, 50),
    "jamon": (200, 200),
    "segundo pan": (350, 200)
}

ingredient_rects = {
    name: image.get_rect(topleft=ingredient_positions[name]) for name, image in ingredient_images.items()
}

plate = pygame.Rect(300, 400, 200, 50)
plate_color = purple_pastel

plate_contents = []

running = True
dragging = False
dragging_item = None

while running:
    screen.fill(WHITE)
    screen.blit(background_image, (0, 0))

    screen.blit(chef_image, chef_rect)
    screen.blit(play_button, play_button_rect)
    screen.blit(text, text_rect)

    for ingredient_name, ingredient_rect in ingredient_rects.items():
        screen.blit(ingredient_images[ingredient_name], ingredient_rect)

    pygame.draw.rect(screen, plate_color, plate)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:
            for ingredient_name, ingredient_rect in ingredient_rects.items():
                if ingredient_rect.collidepoint(event.pos):
                    dragging = True
                    dragging_item = ingredient_name
                    break
        elif event.type == pygame.MOUSEBUTTONUP and event.button == 1:
            if dragging:
                if plate.colliderect(ingredient_rects[dragging_item]):
                    plate_contents.append(ingredient_images[dragging_item])
                dragging = False
                dragging_item = None

    if dragging:
        ingredient_rects[dragging_item].center = pygame.mouse.get_pos()

    for ingredient in plate_contents:
        screen.blit(ingredient, plate)

    pygame.display.flip()

pygame.quit()
sys.exit()






