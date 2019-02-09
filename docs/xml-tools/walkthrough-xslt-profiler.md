---
title: 'Procédure pas à pas : Profileur XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1866500fc4b04622aeb469f663b3b3893ca89c80
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954541"
---
# <a name="walkthrough-xslt-profiler"></a>Procédure pas à pas : Profileur XSLT

Le Générateur de profils XSLT crée des rapports de performances XSLT détaillés qui vous permettent de mesurer, d'évaluer et de cibler les problèmes liés aux performances dans le code XSLT. Le Générateur de profils XSLT inclut des conseils utiles pour les optimisations de feuille de style XSL et XSLT. Pour les applications XSLT qui demandent des performances maximales, cet outil peut être essentiel.

## <a name="prerequisites"></a>Prérequis

Les procédures décrites dans la procédure pas à pas suivante nécessitent Visual Studio et .NET Framework version 4.0 ou ultérieure.

### <a name="create-the-performance-report"></a>Créer le rapport de performances

1.  Ouvrez un document XSLT dans Visual Studio.

2.  Cliquez sur le **profil XSLT** option est disponible dans le menu XML.

3.  Fournissez un document XML d'entrée. Si un document XML n'est pas déjà ouvert, vous êtes invité à entrer le fichier.

4.  L'analyse démarre, et une barre de progression affiche la progression dans l'éditeur.

5.  La sortie XSLT est visible dans le panneau de sortie.

6.  Au terme d'une session de performance, examinez le rapport de performances. Les données enregistrées dans un rapport de performances vous permet d'afficher et d'analyser les performances XSLT.

### <a name="get-all-the-available-views"></a>Obtenir toutes les vues disponibles

1.  Cliquez sur le **affichage actuel** liste déroulante pour obtenir toutes les vues disponibles.

2.  Sélectionnez le **vue Résumé** option dans le **affichage actuel** liste déroulante. Par défaut, un rapport de performances est affiché dans le **vue Résumé**. Cette vue sert de point de départ pour déterminer les problèmes de performances avec les documents XSLT. Le **vue Résumé** répertorie les points de données suivants :

    -   Majorité des fonctions appelées

    -   Fonctions faisant le plus de travail individuel

    -   Fonctions les plus longues à exécuter

3.  Par défaut, il y a trois colonnes pour chaque point de données : le nom de la fonction, le nombre d'appels en valeur absolue, et une valeur en pourcentage de la fonction nommée par rapport au nombre total d'appels de fonction. À partir de données de chaque point dans le **vue Résumé**, vous pouvez accéder à des vues plus détaillées en cliquant sur les points de données de fonction.

4.  Sélectionnez le **affichage fonction** option dans le **affichage actuel** liste déroulante. Le **affichage fonction** répertorie les fonctions appelées lors du profilage. Vous pouvez trier les données en cliquant sur un nom de colonne. Les colonnes affichées par défaut sont les suivantes :

    -   **Nom de la fonction**

    -   **Temps inclusif écoulé**

    -   **Temps exclusif écoulé**

    -   **Temps inclusif d’application**

    -   **Temps exclusif d’application**

    -   **Nombre d’appels**

5.  Toutes les colonnes d'heure sont affichées en valeurs absolues et en pourcentages. Le terme **exclusif** fait référence à la durée totale, une fonction passé à l’exécution exclusion de temps passé par d’autres fonctions appelée pendant l’exécution de cette fonction.

6.  Le terme **inclusif** fait référence au temps total d’une fonction de l’exécution, y compris le temps d’exécution de toutes les fonctions appelées et qu’aucune de ces fonctions appelées appelé autres fonctions.

### <a name="select-callercallee-view"></a>Sélectionner la vue Appelant/Appelé

1.  Sélectionnez **appelant/appelé** afficher dans le **affichage actuel** liste déroulante.

2.  Le **appelant/appelé** vue possède trois parties distinctes suivantes :

    -   **Fonctions qui ont appelé**: Toutes les fonctions qui ont appelé une fonction particulière sont répertoriées dans la partie supérieure de la vue.

    -   **Fonction active**: La fonction particulière qui a été appelée est répertoriée dans la partie centrale de la vue.

    -   **Fonctions qui ont été appelées par** : Toutes les fonctions qui ont été appelées par la fonction particulière sont répertoriées dans la partie inférieure de la vue.

3.  Si une fonction nommée `SyncToNavigator` apparaît dans la partie centrale de la vue, toutes les fonctions qui ont appelé la fonction `SyncToNavigator` s'affichent dans la partie supérieure de la vue et toutes les fonctions appelées par la fonction `SyncToNavigator` s'affichent dans la partie inférieure de la vue.

4.  Vous pouvez modifier la fonction dans la partie centrale de la vue en double-cliquant sur une des fonctions répertoriées dans les autres parties de la vue. La vue est mise à jour automatiquement pour refléter les modifications.

5.  Vous pouvez aussi trier les données en cliquant sur les noms de colonnes.

### <a name="select-call-tree-view"></a>Sélectionnez la vue arborescence des appels

1.  Sélectionnez **vue arborescence des appels** dans le **affichage actuel** liste déroulante. Cette vue est une arborescence de l’exécution du programme.

2.  Le **vue arborescence des appels** affiche la racine de l’arborescence en tant que le nom du processus. Les fonctions sont les nœuds de l’arborescence. Cette vue vous permet d'explorer des traces d'appels spécifiques et d'analyser les traces qui affectent le plus les performances. La vue est similaire à la **vue pile des appels** disponible pendant le débogage. En plus des colonnes dans le **fonction vue**, dans le **vue arborescence des appels**, il existe une colonne supplémentaire pour afficher le **nom du Module**.

3.  Sélectionnez **marques** dans le **affichage actuel** liste déroulante.

4.  Avec le Générateur de profils SLT, des marques apparaissent dans le flux de collection de données avec un commentaire associé. Les marques sont emplacements dans le code qui ont des compteurs. Lorsque vous indiquez au Générateur de profils SLT de collecter des compteurs de performance XSLT, ceux-ci sont collectés chaque fois que l'une de ces marques est exécutée. Les données sont affichées dans une table qui contient le **ID de marque**, **nom de la marque** (**démarrer le programme**, **fin du programme**) et le  **Horodatage**. Les marques ne sont pas regroupées et apparaissent dans l’ordre chronologique dans le **vue marques** du rapport de performances.

### <a name="select-modules-in-the-current-view"></a>Sélectionner des modules dans l'affichage actuel

1.  Sélectionnez **Modules** dans le **affichage actuel** liste déroulante.

2.  La vue de modules est une liste plate de toutes les fonctions agrégées au niveau du module. Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module. Vous pouvez trier les données en cliquant sur un nom de colonne. Par défaut, il existe des valeurs absolues et des pourcentages **temps inclusif écoulé**, **temps exclusif écoulé**, **temps inclusif d’Application**, **Temps exclusif d’application**, et **nombre d’appels**.

3.  Sélectionnez **processus** dans le **affichage actuel** liste déroulante.

4.  La vue processus affiche une table qui inclut le **ID de processus**, **nom de processus**, **heure de début**et le **heure de fin**. Vous pouvez trier les données en cliquant sur les noms de colonnes.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : À l’aide de XSLT hierarchy](../xml-tools/walkthrough-using-xslt-hierarchy.md)