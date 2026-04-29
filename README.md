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
}
Explication :
Cette fonction vérifie si une chaîne est palindrome :
Une file (queue) donne l’ordre normal
Une pile inverse l’ordre
On compare les deux moitiés
  Si identiques → palindrome
  Complexité : O(n)xplication :
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
}
Explication :
Cette fonction libère toute la mémoire :
On supprime chaque nœud un par un
On avance jusqu’à la fin de la liste
 Complexité : O(n)

✅ Exercice 6 :
typedef struct stack {
    int data;
    struct stack *next;
} STACK;

void push(STACK **head, int value)
{
    STACK *node = (STACK*) malloc(sizeof(STACK));

    node->data = value;
    node->next = *head;
    *head = node;
}

int pop(STACK **head)
{
    STACK *tmp = *head;
    int val = tmp->data;

    *head = tmp->next;
    free(tmp);

    return val;
}

STACK * PairImpair(STACK *P1)
{
    STACK *P2 = NULL;
    STACK *P3 = NULL;

    while (P1)
    {
        int val = pop(&P1);

        if (val % 2 == 0)
            push(&P2, val);
        else
            push(&P3, val);
    }

    while (P3)
        push(&P2, pop(&P3));

    return P2;
}
Explication :
Cette fonction sépare les nombres pairs et impairs :
P1 est dépilée
Les pairs vont dans P2
Les impairs dans P3 puis transférés vers P2
  Complexité : O(n)

✅ Exercice 7 :
int EstPalindrome(char chaine[])
{
    int n = strlen(chaine);
    int mid = n / 2;

    STACK *p = NULL;
    struct queue *Q = EcrireMessage(chaine);

    char c1, c2;
    int i;

    for (i = 0; i < mid; i++)
    {
        dequeue(Q, &c1);
        push(&p, c1);
    }

    if (n % 2 != 0)
        dequeue(Q, &c1);

    for (i = 0; i < mid; i++)
    {
        dequeue(Q, &c1);
        c2 = pop(&p);

        if (c1 != c2)
            return 0;
    }

    return 1;
}
 Explication :
Cette fonction vérifie si une chaîne est palindrome :
Une file (queue) donne l’ordre normal
Une pile inverse l’ordre
On compare les deux moitiés
  Si identiques → palindrome
  Complexité : O(n)
