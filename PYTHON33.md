import os
import random
import time


largeur, hauteur = 50, 20


position_x= random.randint(0,largeur)

position_y=0


piece = "|*****|"


def effacer_piece():
    for i in range(7):
        for j in range(7):
            if 0 <= position_x + j < largeur and 0 <= position_y + i < hauteur:
                zone_de_jeu[position_y + i][position_x + j] = ' '


def afficher_zone_de_jeu():
    os.system('clear' if os.name == 'posix' else 'cls')
    for ligne in zone_de_jeu:
        print(''.join(ligne))
    print('-' * (largeur + 2))


zone_de_jeu = [[' ' for _ in range(largeur)] for _ in range(hauteur)]


while True:
     
    effacer_piece()
    but=hauteur-1
    if position_y<but:
    
        position_y += 1

     
    for i in range(7):
        for j in range(7):
            if 0 <= position_x + j < largeur and 0 <= position_y + i < hauteur:   
                if 0 <= i * 7 + j < len(piece):   
                    zone_de_jeu[position_y + i][position_x + j] = piece[i * 1 + j]

    afficher_zone_de_jeu()

    
    time.sleep(0.5)
