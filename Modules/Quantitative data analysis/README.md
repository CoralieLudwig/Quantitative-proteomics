This folder contains the modules dedicated to the quantitative data analysis. They all take as input the standardized format (see "Parsers" folder).
<br/>
<br/>

- ***QC :***<br/>

This module generates a report of quality and reproducibility of data in quantification matrix.

- ***DA :***<br/>

This module, after filtering proteins, normalizing intensities and imputing missing values, executes a differential analysis on quantification matrix. The worklow can be configured thanks to the following parameters :

| Paramètre | Fonction | Valeurs possibles |
| --------- | --------- | --------- |
| Normalisation | Choisir de normaliser les données ou de sauter cette étape | T / F |
| Filter.threshold.ms | Nombre minimal d’identifications par MS/MS pour que la protéine soit conservée pour l’analyse | ℕ  |
| Filter.threshold.obs | Pourcentage minimal d’observations dans au moins une condition pour la protéine soit conservée pour l’analyse. | {0,100} |
| Imputation.MNAR.model | Choix du modèle pour l’imputation des MNAR | percentile / gaussian |
| Imputation.MNAR.percentile | Si le modèle “percentile” est choisi pour l’imputation des  MNAR, choix du percentile | {0,1} |
| Imputation.MCAR.model | Choix du modèle pour l’imputation des MCAR | none / MNAR / knn |
| Imputation.MCAR.threshold.obs | Nombre d’observations minimal dans la condition pour qu’une valeur manquante soit considérée comme MCAR | {0, nombre de réplicats} |
| Imputation.MCAR.threshold.MSMS | Nombre d’identification par MS/MS minimal dans la condition pour qu’une valeur manquante soit considérée comme MCAR | {0, nombre de réplicats} |
| Imputation.knn.min.occurrences | Nombre d’observations minimal dans la condition pour qu’une protéine puisse être utilisée comme un k plus proche voisin | {0, nombre de réplicats} |
| Test.type | Choix du test statistique à exécuter | t.test / limma / wilcoxon |
| Test.log | Choisir de transformer les intensités par le log pour réaliser le test statistique ou non | T / F |
| Test.alternative | Choisir si le test sera unilatéral ou bilatéral | two.sided / unilateral |
| Test.paired | Choisir si le test sera apparié ou non | T / F |
| Test.var.equal | En cas de choix du t.test, préciser si les variances sont égales dans le jeu de données. Si oui, un test de Student sera utilisé, sinon le test de Welch sera utilisé. | T / F |
| Test.adjust.procedure | Choix de la méthode de correction de tests multiples | none / BH / ABH |
| Test.adjust.FDR | Choix du FDR accepté pour la correction de tests multiples | {0,1} |
| Ratio | Choix de la métrique pour les ratios du volcano-plot | fc / zscore |
| Volcano.threshold.pvalue | Seuil de significativité pour la p-valeur | {0,1} |
| Volcano.threshold.ratio | Seuil de significativité pour le ratio | ℝ |
| Comparisons | Liste des paires de conditions à comparer | Exemple : 50fmol/25fmol;50fmol/10fmol |
| Figure.format | Choisir le format des figures du rapport généré | SVG / JPEG |

Here you can see an example of parameters file : .
<br/>
The experimental also have to be provided as an input. Here you can see an example of experimental design file : .
<br/>
The module gives as outputs a TSV table summarizing input data, intensities after each step of processing and final results of statistical results. A report containg QC figures for each processing step and figures showing the results of differential analysis is also provided.