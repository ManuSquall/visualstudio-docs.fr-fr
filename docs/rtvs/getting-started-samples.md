---
title: Exemples de projets Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Exemples de projets Outils R pour Visual Studio

Cette collection d’exemples vous permet de vous familiariser avec R, Outils R pour Visual Studio (RTVS) et Microsoft R Server :

1. Téléchargez le [fichier zip d’exemples](https://github.com/Microsoft/RTVS-docs/archive/master.zip) et extrayez son contenu vers le dossier de votre choix.
1. Ouvrez `examples/Examples.sln`. Le projet comprend deux dossiers :

    - *A First Look at R* (Présentation de R) est une introduction destinée aux débutants qui expose clairement les bases de R.
    - *MRS and Machine Learning* (MRS et Machine Learning) donne des exemples d’utilisation de R et de Microsoft R Server pour Machine Learning.

## <a name="a-first-look-at-r"></a>A First Look at R (Présentation de R)

Cet exemple propose une introduction approfondie de R avec des commentaires détaillés dans les fichiers sources. Pour exploiter au mieux ces deux exemples, placez le curseur en haut du fichier, puis appuyez sur Ctrl+Entrée pour envoyer une par une les lignes à la fenêtre **R Interactive** qui affiche les résultats. Notez que certaines lignes installent des packages, ce qui peut prendre une minute ou deux.

- `1-Getting Started with R.R` couvre de nombreux principes fondamentaux de R, notamment l’utilisation de packages, le chargement et l’analyse des données, ainsi que le traçage.

    ![Exemple de sortie de l’exemple 1-Getting Started with R.R](~/docs/rtvs/media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` présente le package graphique ggplot2 connu pour ses beaux graphiques et sa syntaxe simple. Cet exemple permet de visualiser des données sur les tremblements de terre à Fidji.

    ![Exemple de sortie de l’exemple 2-Introduction to ggplot2.R](~/docs/rtvs/media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server et Machine Learning

Cette collection d’exemples montre comment utiliser R et Microsoft R Server pour créer des modèles de Machine Learning, puis comment tirer parti des fonctionnalités de [Microsoft R Server (MRS)](http://aka.ms/rtvs-msft-r). Notez que vous devez installer MRS pour exécuter les scripts comprenant `MRS` dans le titre et où c’est mentionné.

Le meilleur moyen de découvrir un exemple, quel qu’il soit, consiste à ouvrir le fichier, à placer le curseur en haut du code, puis à exécuter le code ligne par ligne avec Ctrl+Entrée. Pour plus de détails, consultez également les fichiers Markdown dans chaque dossier.

- `Benchmarks` exécute plusieurs benchmarks nécessitant beaucoup de ressources système pour montrer les gains de performance qui découlent de l’utilisation de Microsoft R Open et d’Intel Math Kernel Library (MKL) dans le cadre de l’exécution de calculs parallèles d’algèbre linéaire. Basé sur des données simulées, il compare spécifiquement le nombre de threads utilisés, un ou deux, pour effectuer certains calculs liés aux matrices.   

    ![Exemple de tracé de benchmark](~/docs/rtvs/media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` crée un modèle de prévision de demande de location de vélos selon un jeu de données d’historique à l’aide de Microsoft R Server. 

- `Data_Exploration` contient trois scripts :  
    - `Import Data from URL.R` montre comment charger un fichier de données identifié par URL dans R.
    - `Import Data from URL to xdf.R` montre comment charger un fichier de données identifié par URL dans Microsoft R Server en tant que fichier xdf. (Nécessite MRS.)
    - `Using ggplot2.R` est une extension de l’exemple `A First Look at R/2-Introduction to ggplot2.R`. Il traite de manière plus approfondie des fonctionnalités de ggplot2, notamment le traçage 3D interactif.

        ![Sortie de l’exemple Using ggplot2.R](~/docs/rtvs/media/samples-3d-interactive.png)

- `Datasets` contient trois fichiers `.csv` utilisés par d’autres exemples.
- `Flight_Delays_Prediction_with_R` et `Flight_Delays_Prediction_with_MRS` montrent comment prédire les vols en retard à l’aide de R, de Machine Learning et des données d’historique sur les vols à l’heure et la météo. 
- `Machine learning` contient trois exemples mettant en œuvre R et MRS pour résoudre de vrais problèmes, comme la prédiction des vols en retard, des prix immobiliers et des locations de vélos. Ces exemples vous montrent également comment utiliser plusieurs modèles Machine Learning populaires et comment les déployer en tant que service web Azure à l’aide d’un espace de travail [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/).

- `R_MRO_MRS_Comparison` est une comparaison en six parties qui présente les similitudes et les différences entre R, Microsoft R Open et Microsoft R Server. Cette comparaison porte sur les commandes, la syntaxe, les constructions et les performances.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Quelles sont les particularités de Microsoft R Open et de Microsoft R Server ?

[Microsoft R Open](http://aka.ms/rtvs-r-open), distribution Microsoft de R, présente deux différences importantes avec [CRAN R](https://cran.r-project.org/) :

1. [De meilleures performances de calcul](https://mran.revolutionanalytics.com/rro/#intelmkl1) avec les bibliothèques [Intel Math Kernel Libraries](https://software.intel.com/intel-mkl). Celles-ci sont disponibles en téléchargement gratuit sur le site web de Microsoft pour une utilisation avec Microsoft R Open.

1. Un [Toolkit R reproductible](https://mran.revolutionanalytics.com/rro/#reproducibility) qui garantit que les bibliothèques que vous avez utilisées pour générer votre programme R sont accessibles à d’autres personnes souhaitant reproduire votre travail.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) est une extension de R qui vous permet de gérer davantage de données plus rapidement. Il offre à R deux fonctionnalités puissantes :

1. Des jeux de données plus grands. MRS peut traiter les données hors mémoire à partir de diverses sources, notamment les clusters Hadoop, les bases de données et les entrepôts de données. Vous n’êtes donc plus limité par votre mémoire RAM.

1. Traitement parallèle et multicœur. MRS peut distribuer efficacement les calculs sur toutes les ressources de calcul disponibles. Sur votre poste de travail personnel ou un cluster distant, MRS obtient plus rapidement une réponse.

La comparaison suivante montre que MRS et MRO avec MKL offrent des performances de calcul nettement supérieures à celles obtenues par R et MRO sans MKL pour certains calculs de matrice. Des données simulées sont utilisées dans ce calcul :

![Comparaison entre, d’une part, MRS et MRO avec MKL et, d’autre part, R et MRO sans MKL](~/docs/rtvs/media/samples-speed-comparison.png)

Pour obtenir une comparaison technique de R avec MRO et MRS, lisez la [discussion approfondie de Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) sur le sujet.

La figure suivante compare ensuite la durée calendaire en secondes utilisée dans la création de modèles de régression logistique pour prédire si l’arrivée de vols passagers réguliers sera retardée de plus de 15 minutes. La durée calendaire dans CRAN R augmente considérablement à la suite d’une légère augmentation du nombre de lignes, tandis que la durée calendaire dans MRS n’est multipliée que par deux environ. Pour plus d’informations sur ce benchmark, passez en revue l’exemple `Benchmarks/rxGlm_benchmark.R`.

![Benchmark rxGlm](~/docs/rtvs/media/samples-rxGLM-benchmark.png)

