# Spil

def initialize_game(pygame, clock, screen):
    BreddeGange2 = 110
    bredde = 55


    pygame.draw.line(screen, (92, 0, 0), [57, 175], [1719, 175], bredde)
    pygame.draw.line(screen, (92, 0, 0), [570, 105], [1, 45], bredde)
    pygame.draw.line(screen, (92, 0, 0), [157, 300], [1874, 300], bredde)
    pygame.draw.rect(screen, (92, 0, 0), [184, 273, 1, 375], bredde)
    pygame.draw.rect(screen, (92, 0, 0), [184, 700, 1, 375], bredde)
    pygame.draw.rect(screen, (92, 0, 0), [320, 373, 1, 600], bredde)
    pygame.draw.rect(screen, (92, 0, 0), [484, 273, 1, 375], bredde)
    pygame.draw.rect(screen, (92, 0, 0), [484, 700, 1, 375], bredde)

    # Kanterne:
    pygame.draw.rect(screen, (100, 0, 255), [1, 1, 1919, 1], BreddeGange2)
    pygame.draw.rect(screen, (100, 0, 255), [1, 1, 1, 1079], BreddeGange2)
    pygame.draw.rect(screen, (100, 0, 255), [1915, 1, 1, 1079], BreddeGange2)
    pygame.draw.rect(screen, (100, 0, 255), [1, 1079, 1919, 55], BreddeGange2)


    #pygame.display.flip()
    #clock.tick(60)
    # pygame.draw.rect(screen,(0,0,0),[1803,175,130,1], 55)
    # pygame.draw.rect(screen, (0, 0, 0), [0, 300, 130, 1], 55)


def spil(pygame, clock, screen):
    done = False
    is_blue = True
    x = 0
    y = 0
    o=2
    

    #dir_path = os.path.dirname(os.path.realpath(__file__))
    #print (dir_path)
    initialize_game(pygame, clock, screen)
    Blob = pygame.image.load('C:/Users/rasmu/PycharmProjects/programmering/venv/blob2.png')
    #Blob er 392,272
    #Blob = pygame.transform.scale(Blob,(85,65))
    while not done:
        pygame.time.wait(10)
        # Get key pressed from user
        pressed = pygame.key.get_pressed()
        if pressed[pygame.K_UP]: y -= 4
        if pressed[pygame.K_DOWN]: y += 4
        if pressed[pygame.K_LEFT]: x -= 4
        if pressed[pygame.K_RIGHT]: x += 4



        # if outside border move back in
        #if y < o:
        #    y = y + 20
        #if x < o:
        #    x = x + 20

        # Fill background with black color
        screen.fill((0, 0, 0))

        initialize_game(pygame, clock, screen)

        # Draw blob image onto screen
        screen.blit(Blob, (x, y))
        clock.tick(3600)


        # Draw circle
        pygame.draw.circle(screen, (2, 145, 145), [x, y], 10)
        pygame.display.update()
        for event in pygame.event.get():

            if event.type == pygame.QUIT:
                done = True
            if event.type == pygame.KEYDOWN and event.key == pygame.K_ESCAPE:
                done = True


# MAIN
import pygame
import os
clock = pygame.time.Clock()
screen = pygame.display.set_mode((0,0), pygame.FULLSCREEN)
pygame.init()


spil(pygame, clock, screen)
