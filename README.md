Exercice 1 : Insertion en têtestruct Element {
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
}Explication :
Cette fonction insère un nouvel élément au début de la liste :
On crée un nouveau nœud
On le relie à l’ancien premier élément
On met à jour la tête de la liste
 Complexité : O(1)