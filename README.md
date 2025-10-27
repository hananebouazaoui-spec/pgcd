# pgcd
Travaux Pratiques – Algorithme d’Euclide (PGCD
Réalisé par : Hanane Bouazaoui
École : ESTK
Date de remise : 29/10/2025
✓Définition : Le PGCD de deux entiers naturels est le plus grand entier qui divise les deux nombres sans reste.
✓Principe : Si a et b sont deux entiers, alors :PGCD(a, b) = PGCD(b, a mod b)On répète jusqu’à ce que le reste soit nul.
°Exemple : 
Calculons PGCD(252, 105)252 = 
105 * 2 + 42105 = 42 * 2 + 2142 = 21 * 2 + 0➡️ PGCD = 21