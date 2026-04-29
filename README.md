✅Exercice 1 : Insertion en têtestruct Element {
    int val;
    struct Element *suivant;
};

typedef struct Element LISTE;

int InsererElementEnTete(LISTE **L, int valeur)
{
    LISTE *element = (LISTE*) malloc(sizeof(LISTE));

    if (element == NULL)
    {
        printf("Probleme d’allocation memoire\n");
        return 0;
    }

    element->val = valeur;
    element->suivant = *L;
    *L = element;

    return 1;
}
Explication :
Cette fonction insère un nouvel élément au début de la liste :
On crée un nouveau nœud
On le relie à l’ancien premier élément
On met à jour la tête de la liste
 Complexité : O(1)
✅ Exercice 2:
int RechercherValeur(LISTE *L, int valeur)
{
    LISTE *ptr = L;

    while (ptr != NULL)
    {
        if (ptr->val == valeur)
            return 1;

        ptr = ptr->suivant;
    }

    return 0;
}
 EXPLICATION:
Cette fonction cherche une valeur dans la liste :
On parcourt chaque nœud
On compare chaque valeur
Si trouvé → 1 sinon → 0
  Complexité : O(n)
✅ Exercice 3 :
int SuppressionValeurMin(LISTE **L)
{
    if (*L == NULL)
        return 0;

    LISTE *ptr = *L;
    LISTE *pMin = *L;
    LISTE *pPrec = NULL;
    LISTE *pPrecMin = NULL;

    int minim = ptr->val;

    while (ptr != NULL)
    {
        if (ptr->val < minim)
        {
            minim = ptr->val;
            pMin = ptr;
            pPrecMin = pPrec;
        }
        pPrec = ptr;
        ptr = ptr->suivant;
    }

    if (pPrecMin == NULL)
        *L = pMin->suivant;
    else
        pPrecMin->suivant = pMin->suivant;

    free(pMin);

    return 1;
}
  Explication :
Cette fonction supprime le plus petit élément :
On cherche la valeur minimale
On garde son adresse et celle du précédent
On enlève le nœud de la liste
 Complexité : O(n)
✅ Exercice 4 :
LISTE * Fusion(LISTE *L1, LISTE *L2)
{
    if (!L1) return L2;
    if (!L2) return L1;

    LISTE *p1 = L1;
    LISTE *p2 = L2;
    LISTE *L = L1;

    LISTE *p3;
    LISTE *p4;

    while (p1 != NULL && p2 != NULL)
    {
        p3 = p1->suivant;
        p1->suivant = p2;

        p4 = p2->suivant;
        p2->suivant = p3;

        p1 = p3;
        p2 = p4;
    }

    return L;
}Explication :
Cette fonction fusionne deux listes en alternant les éléments :
On relie un élément de L1 puis un de L2
On ne crée pas de nouveaux nœuds
On modifie فقط les pointeurs
 Complexité : O(n)
✅ Exercice 5 :
void DestructionListe(LISTE **L)
{
    LISTE *ptr;

    while (*L != NULL)
    {
        ptr = *L;
        *L = (*L)->suivant;
        free(ptr);
    }
}Explication :
Cette fonction libère toute la mémoire :
On supprime chaque nœud un par un
On avance jusqu’à la fin de la liste
 Complexité : O(n)
