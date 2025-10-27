# pgcd
Travaux Pratiques – Algorithme d’Euclide (PGCD
Réalisé par : Hanane Bouazaoui
École : ESTK
Date de remise : 29/10/2025
✓Définition : Le PGCD de deux entiers naturels est le plus grand entier qui divise les deux nombres sans reste.
✓Principe : Si a et b sont deux entiers, alors :PGCD(a, b) = PGCD(b, a mod b)On répète jusqu’à ce que le reste soit nul.
°Exemple 1: 
Calculons PGCD(270,192)
270=192×1+78
192=78×2+36
78=36×2+6
36=6×6+0➡️PCGD=6
°Exemple 2:
calculons PCGD(17,13)
17=13×1+4
13=4×3+1
4=4×1+0➡️PCGD=1
✓Implémentation en langage C:
