import os
import random
import time

# Dimensions de la zone de jeu
largeur, hauteur = 50, 20

# Position initiale de la pièce
position_x= random.randint(0,largeur)
# Ajustement de la position initiale
position_y=0

# Caractère de la pièce Tetris
piece = "|*****|"

# Fonction pour effacer la pièce de la zone de jeu
def effacer_piece():
    for i in range(7):
        for j in range(7):
            if 0 <= position_x + j < largeur and 0 <= position_y + i < hauteur:  # Vérifier les limites
                zone_de_jeu[position_y + i][position_x + j] = ' '

# Fonction pour afficher la zone de jeu
def afficher_zone_de_jeu():
    os.system('clear' if os.name == 'posix' else 'cls')
    for ligne in zone_de_jeu:
        print(''.join(ligne))
    print('-' * (largeur + 2))

# Créer une matrice vide pour la zone de jeu
zone_de_jeu = [[' ' for _ in range(largeur)] for _ in range(hauteur)]

# Boucle de jeu
while True:
    # Effacer la pièce de la zone de jeu
    effacer_piece()
    but=hauteur-1
    if position_y<but:
    # Déplacer la pièce vers le bas
        position_y += 1

    # Afficher la pièce dans la nouvelle position
    for i in range(7):
        for j in range(7):
            if 0 <= position_x + j < largeur and 0 <= position_y + i < hauteur:  # Vérifier les limites
                if 0 <= i * 7 + j < len(piece):  # Vérifier les limites de l'index de la pièce
                    zone_de_jeu[position_y + i][position_x + j] = piece[i * 1 + j]

    afficher_zone_de_jeu()

    # Délai pour contrôler la vitesse du jeu
    time.sleep(0.5)
