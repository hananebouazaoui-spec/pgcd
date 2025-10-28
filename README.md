# pgcd
Travaux Pratiques – Algorithme d’Euclide (PGCD
Réalisé par : Hanane Bouazaoui
École : ESTK
Date de remise : 29/10/2025

    ✓Définition : Le PGCD de deux entiers naturels est le plus grand entier qui divise les deux nombres sans reste.

    ✓Principe : Si a et b sont deux entiers, alors :PGCD(a, b) = PGCD(b, a mod b)On répète jusqu’à ce que le reste soit nul.
  2■■Exemles manuelles;
  °Exemple 1: 
Calculons PGCD(270,192)
270=192×1+78
192=78×2+36
78=36×2+6
36=6×6+0
➡️ PCGD=6
   °Exemple 2:
calculons PCGD(17,13)
17=13×1+4
13=4×3+1
4=4×1+0
➡️ PCGD=1

   °Exemple 3:
calculons PCGD(48,18)
48 = 18×2 + 12
18 = 12×1 + 6
12 = 6×2 + 0
➡️ PGCD = 6
   °Exemple 4: 
calculons PCGD(1071,462)
1071 = 462×2 + 147
462 = 147×3 + 21
147 = 21×7 + 0
➡️ PGCD = 21
  3■■Algorithme (pseudo-code)
Entrée : deux entiers a, b
Tant que b ≠ 0 faire
r ➡️ a mod b
a ➡️ b
b ➡️ r
Fin Tant que
Sortie : a (le PGCD)
  4■■ Implémentation en langage C
function gcd(a, b):
    while b ≠ 0:
        r = a mod b
        a = b
        b = r
    return a