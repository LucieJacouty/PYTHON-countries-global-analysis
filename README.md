# Etude de marché globale afin de définir des pays cibles d'exportation
 
Projet Openclassrooms - Formation Data Analyst  

Objectif : Au sein d'une entreprise agroalimentaire, effectuer une première étude de marché afin de définir des pays cibles pour une expansion à l'international  
Choix d'effectuer une analyse très large qui fait un "état de santé" des pays  

Contenu :
- Data : toutes les données utilisées (5 datasets) 
- Notebook : le notebook jupyter regroupant toutes les analyses

Utilisation des librairies : Numpy, Pandas, Matplotlib, Seaborn, Scipy et Scikit-learn 

## Préparation des données 

Récupération de nombreux indicateurs sur le site de la Banque Mondiale (importations, exportations, PIB, PNB, endêtemment, taux de chômage, etc.)  
Au final -> 173 individus (pays) pour 36 variables  


## ACP (Analyse en Composantes Principales) 

But = Réduire le nombre de variables  
Réalisé avec scikit-learn  

Préparation : 
- Remplacer les valeurs nulles par la moyenne de la variable
- Normaliser les données (réduire et centrer) 

### Choix du nombre de composantes

Déterminer un nombre de composantes optimal, différentes méthodes : 
- Méthode du coude : ébouli des valeurs propres 
- Méthode de la variance expliquée : ébouli des valeurs propres avec somme cumulée de la variance 
- Méthode des valeurs propres ou règle de Kaiser : composantes dont la valeur propre est supérieur 1
- Méthode des bâtons brisées (Frontier et Legendre-Legendre) : calcul d'une valeur seuil pour chaque axe d’inertie, comparaison du seuil à la valeur propre 

Au final, choix de 9 composantes 

### Représentations sur le 1er plan factoriel 

Représentation des individus   
Calcul de la contribution des individus aux axes   
Calcul de la corrélation des variables avec les axes   
Représentation du cercle de corrélation des variables    
Calcul de la contribution des variables aux axes   

Au final, croisement des contributions et corrélations pour "nommer" les 9 composantes 


## Classification Ascendante Hiérarchique  

Réalisé avec scipy  

Première étude de la manière dont les pays sont groupés 


## Clustering  

Réalisé avec scikit-learn  

Déterminer le nombre de clusters : 
- Méthode du coude, similaire à l’ACP  
- Calcul d’une inertie ajustée  
- Coefficient de silhouette, compris entre -1 et 1  

Au final, choix de 12 clusters  

Réalisation du clustering  
Projection des individus sur le 1er plan factoriel  
Projection des centroïdes sur le 1er plan factoriel  
5 centroïdes = 5 clusters 

Réalisation d'un heatmap croisant composantes/clusters  

2 composantes idéales pour notre étude -> 5 clusters possible à viser   
Cluster le plus intéressant : cluster 4, 33 pays. Europe de l’Est, Sud et Nord (Albanie, Autriche, Bulgarie, Croatie, Danemark, Finlande, Grèce, Norvège, Suède, etc.) 
