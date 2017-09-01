---
title: Exemples de projets Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: ec9862f9e7fcbd084d5e12c0467c8b608a5b4956
ms.contentlocale: fr-fr
ms.lasthandoff: 07/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Exemples de projets Outils R pour Visual Studio

Cette collection d’exemples vous permet de vous familiariser avec R, Outils R pour Visual Studio (RTVS) et Microsoft R Server :

1. Téléchargez le [fichier zip d’exemples](https://github.com/Microsoft/RTVS-docs/archive/master.zip) et extrayez son contenu vers le dossier de votre choix.
1. Ouvrez `examples/Examples.sln` pour afficher deux dossiers dans le projet :

    - *A First Look at R* (Présentation de R) est une introduction destinée aux débutants qui expose clairement les bases de R.
    - *MRS and Machine Learning* (MRS et Machine Learning) donne des exemples d’utilisation de R et de Microsoft R Server pour Machine Learning.

## <a name="a-first-look-at-r"></a>A First Look at R (Présentation de R)

Cet exemple propose une introduction approfondie de R avec des commentaires détaillés dans deux fichiers sources. Pour en tirer le meilleur parti, placez le curseur en haut du fichier et appuyez sur Ctrl+Entrée pour envoyer une par une les lignes de code à la **Fenêtre interactive R**. (Certaines lignes installent des packages, ce qui peut prendre une minute ou deux.)

- `1-Getting Started with R.R` couvre de nombreux principes fondamentaux de R, notamment l’utilisation de packages, le chargement et l’analyse des données, ainsi que le traçage.

    ![Exemple de sortie de l’exemple 1-Getting Started with R.R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` présente le package graphique ggplot2 connu pour ses beaux graphiques et sa syntaxe simple. Cet exemple permet de visualiser des données sur les tremblements de terre à Fidji.

    ![Exemple de sortie de l’exemple 2-Introduction to ggplot2.R](media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server et Machine Learning

Cette collection d’exemples montre comment utiliser R pour créer des modèles Machine Learning, puis comment tirer parti de [MRS (Microsoft R Server)](http://aka.ms/rtvs-msft-r). Installez MRS pour exécuter les scripts comprenant `MRS` dans le titre et là où cela est mentionné.

Comme avec tous les exemples, ouvrez le fichier, placez le curseur en haut, puis exécutez le code ligne par ligne avec Ctrl+Entrée. Les fichiers Markdown dans chaque dossier contiennent également des détails supplémentaires.

- `Benchmarks` exécute plusieurs calculs parallèles d’algèbre linéaire nécessitant beaucoup de ressources système pour montrer les gains de performances qui découlent de l’utilisation de Microsoft R Open et d’Intel Math Kernel Library (MKL). Avec des données simulées, les tests d’évaluation comparent de façon spécifique les calculs liés aux matrices selon le nombre de threads utilisés (un ou deux).

    ![Exemple de tracé de benchmark](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` crée un modèle de prévision de demande de location de vélos selon un jeu de données d’historique à l’aide de Microsoft R Server. 

- `Data_Exploration` contient trois scripts :  
    - `Import Data from URL.R` montre comment charger un fichier de données identifié par URL dans R.
    - `Import Data from URL to xdf.R` montre comment charger un fichier de données identifié par URL dans Microsoft R Server en tant que fichier xdf. (Nécessite MRS.)
    - `Using ggplot2.R` est une extension de l’exemple `A First Look at R/2-Introduction to ggplot2.R`. Il traite de manière plus approfondie des fonctionnalités de ggplot2, notamment le traçage 3D interactif.

        ![Sortie de l’exemple Using ggplot2.R](media/samples-3d-interactive.png)

- `Datasets` contient trois fichiers `.csv` utilisés par d’autres exemples.
- `Flight_Delays_Prediction_with_R` et `Flight_Delays_Prediction_with_MRS` montrent comment prédire les vols en retard à l’aide de R, de Machine Learning et des données d’historique sur les vols à l’heure et la météo. 
- `Machine learning` contient trois exemples permettant d’apprendre à prévoir les vols en retard, les prix immobiliers et les locations de vélos. Ces exemples réunis illustrent l’application de R et MRS pour résoudre de vrais problèmes. Ces exemples vous montrent également comment utiliser plusieurs modèles Machine Learning populaires et comment les déployer en tant que service web Azure à l’aide d’un espace de travail [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` est une comparaison en six parties qui présente les similitudes et les différences entre R, Microsoft R Open et Microsoft R Server. Cette comparaison porte sur les commandes, la syntaxe, les constructions et les performances.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Quelles sont les particularités de Microsoft R Open et de Microsoft R Server ?

[Microsoft R Open](http://aka.ms/rtvs-r-open), distribution Microsoft de R, présente deux différences importantes avec [CRAN R](https://cran.r-project.org/) :

1. [De meilleures performances de calcul](https://mran.revolutionanalytics.com/rro/#intelmkl1) avec les bibliothèques [Intel Math Kernel Libraries](https://software.intel.com/intel-mkl). Les bibliothèques sont disponibles en téléchargement gratuit sur le site web de Microsoft pour une utilisation avec Microsoft R Open.

1. Un [Toolkit R reproductible](https://mran.revolutionanalytics.com/rro/#reproducibility) garantit que les bibliothèques que vous avez utilisées pour générer votre programme R sont toujours accessibles à d’autres personnes souhaitant reproduire votre travail.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) est une extension de R qui vous permet de gérer davantage de données plus rapidement. Il offre à R deux fonctionnalités puissantes :

1. Des jeux de données plus grands, sans limitations de mémoire RAM. MRS peut traiter les données hors mémoire à partir de diverses sources, notamment les clusters Hadoop, les bases de données et les entrepôts de données.

1. Traitement parallèle et multicœur. MRS peut distribuer efficacement les calculs sur toutes les ressources de calcul disponibles. Sur votre poste de travail personnel ou un cluster distant, MRS obtient plus rapidement une réponse.

La comparaison suivante montre que MRS et MRO avec MKL offrent des performances de calcul nettement supérieures à celles obtenues par R et MRO sans MKL pour certains calculs de matrice. Des données simulées sont utilisées dans ce calcul :

![Comparaison entre, d’une part, MRS et MRO avec MKL et, d’autre part, R et MRO sans MKL](media/samples-speed-comparison.png)

Pour obtenir une comparaison technique de R avec MRO et MRS, lisez la [discussion approfondie de Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sur le sujet.

La figure suivante compare ensuite le temps écoulé en secondes utilisé dans la création de modèles de régression logistique pour prévoir les vols en retard de plus de 15 minutes.  Le temps écoulé utilisé dans CRAN R augmente considérablement à la suite d’une augmentation de quelques lignes, tandis que le temps écoulé dans MRS n’est multiplié que par deux environ. Pour plus d’informations sur ce benchmark, passez en revue l’exemple `Benchmarks/rxGlm_benchmark.R`.

![Benchmark rxGlm](media/samples-rxGLM-benchmark.png)

