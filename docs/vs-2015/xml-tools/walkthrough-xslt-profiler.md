---
title: 'Procédure pas à pas : profileur XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669522"
---
# <a name="walkthrough-xslt-profiler"></a>Procédure pas à pas : Générateur de profils XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le Générateur de profils XSLT crée des rapports de performances XSLT détaillés qui vous permettent de mesurer, d'évaluer et de cibler les problèmes liés aux performances dans le code XSLT. Le Générateur de profils XSLT inclut des conseils utiles pour les optimisations de feuille de style XSL et XSLT. Pour les applications XSLT qui demandent des performances maximales, cet outil peut être essentiel.

## <a name="prerequisites"></a>Prérequis
 Les procédures dans la procédure pas à pas suivante nécessitent Visual Studio 2010 et le .NET Framework version 4.0. Le Générateur de profils XSLT est uniquement disponible si Microsoft Visual Studio Team System avec les outils de profilage est installé.

### <a name="create-the-performance-report"></a>Créer le rapport de performances

1. Ouvrez un document XSLT dans Visual Studio.

2. Cliquez sur l’option **Profil XSLT** disponible dans le menu XML.

3. Fournissez un document XML d'entrée. Si un document XML n'est pas déjà ouvert, vous êtes invité à entrer le fichier.

4. L'analyse démarre, et une barre de progression affiche la progression dans l'éditeur.

5. La sortie XSLT est visible dans le panneau de sortie.

6. Au terme d'une session de performance, examinez le rapport de performances. Les données enregistrées dans un rapport de performances vous permet d'afficher et d'analyser les performances XSLT.

### <a name="get-all-the-available-views"></a>Obtenir toutes les vues disponibles

1. Cliquez sur la liste déroulante **affichage actuel** pour obtenir toutes les vues disponibles.

2. Sélectionnez l’option **vue Résumé** dans la liste déroulante **affichage actuel** . Par défaut, un rapport de performances est affiché dans la **vue Résumé**. Cette vue sert de point de départ pour déterminer les problèmes de performances avec les documents XSLT. Le **mode Résumé** répertorie les points de données suivants :

    - Majorité des fonctions appelées

    - Fonctions faisant le plus de travail individuel

    - Fonctions les plus longues à exécuter

3. Par défaut, il y a trois colonnes pour chaque point de données : le nom de la fonction, le nombre d'appels en valeur absolue, et une valeur en pourcentage de la fonction nommée par rapport au nombre total d'appels de fonction. À partir de chaque point de données dans la **vue Résumé**, vous pouvez accéder à des vues plus détaillées en cliquant avec le bouton droit sur les points de données de la fonction.

4. Sélectionnez l’option **affichage des fonctions** dans la liste déroulante **affichage actuel** . La **vue fonction** répertorie les fonctions appelées lors du profilage. Vous pouvez trier les données en cliquant sur un nom de colonne. Les colonnes affichées par défaut sont les suivantes :

    - **Nom de la fonction**

    - **Temps inclusif écoulé**

    - **Temps exclusif écoulé**

    - **Temps inclusif d’application**

    - **Temps exclusif d’application**

    - **Nombre d’appels**

5. Toutes les colonnes d'heure sont affichées en valeurs absolues et en pourcentages. Le terme **exclusive** fait référence au temps total passé par une fonction à exécuter un temps d’exécution exclusif passé par d’autres fonctions appelées pendant l’exécution de cette fonction.

6. Le terme **inclus** fait référence à la durée totale d’exécution d’une fonction, y compris la durée d’exécution de toutes les fonctions qu’elle a appelées et si l’une de ces fonctions appelées est appelée autres fonctions.

### <a name="select-callercallee-view"></a>Sélectionner la vue Appelant/Appelé

1. Sélectionnez la vue **appelant/appelé** dans la liste déroulante **affichage actuel** .

2. La vue **appelant/appelé** comprend les trois parties distinctes suivantes :

    - **Fonctions qui ont appelé**: toutes les fonctions qui ont appelé une fonction particulière sont répertoriées dans la partie supérieure de la vue.

    - **Fonction active**: la fonction particulière qui a été appelée est indiquée dans la partie centrale de la vue.

    - **Fonctions qui ont été appelées par** : toutes les fonctions qui ont été appelées par la fonction particulière sont répertoriées dans la partie inférieure de la vue.

3. Si une fonction nommée `SyncToNavigator` apparaît dans la partie centrale de la vue, toutes les fonctions qui ont appelé la fonction `SyncToNavigator` s'affichent dans la partie supérieure de la vue et toutes les fonctions appelées par la fonction `SyncToNavigator` s'affichent dans la partie inférieure de la vue.

4. Vous pouvez modifier la fonction dans la partie centrale de la vue en double-cliquant sur une des fonctions répertoriées dans les autres parties de la vue. La vue est mise à jour automatiquement pour refléter les modifications.

5. Vous pouvez aussi trier les données en cliquant sur les noms de colonnes.

### <a name="select-calltree-view"></a>Sélectionner la vue de l'arborescence des appels

1. Sélectionnez **vue arborescence des appels** dans la liste déroulante **affichage actuel** . Cette vue est une arborescence de l’exécution du programme.

2. La **vue arborescence des appels** affiche la racine de l’arborescence en tant que nom de processus. Les fonctions sont les nœuds de l'arborescence. Cette vue vous permet d'explorer des traces d'appels spécifiques et d'analyser les traces qui affectent le plus les performances. La vue est similaire à la **vue** de la pile des appels disponible pendant le débogage. En plus des colonnes de l' **affichage des fonctions**, dans la **vue arborescence des appels**, il existe une colonne supplémentaire pour afficher le nom du **module**.

3. Sélectionnez **marques** dans la liste déroulante **affichage actuel** .

4. Avec le Générateur de profils SLT, des marques apparaissent dans le flux de collection de données avec un commentaire associé. Les marques sont emplacements dans le code qui ont des compteurs. Lorsque vous indiquez au Générateur de profils SLT de collecter des compteurs de performance XSLT, ceux-ci sont collectés chaque fois que l'une de ces marques est exécutée. Les données sont affichées dans un tableau contenant l' **ID de marque**, le **nom de marque** (**programme de démarrage**, le **programme final**) et l' **horodatage**. Les marques ne sont pas agrégées et apparaissent dans l’ordre chronologique dans la **vue marques** du rapport de performances.

### <a name="select-modules-in-the-current-view"></a>Sélectionner des modules dans l'affichage actuel

1. Sélectionnez **modules** dans la liste déroulante **affichage actuel** .

2. La vue de modules est une liste plate de toutes les fonctions agrégées au niveau du module. Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module. Vous pouvez trier les données en cliquant sur un nom de colonne. Par défaut, il existe à la fois des valeurs absolues et des nombres de pourcentages pour le **temps inclusif écoulé**, temps **exclusif écoulé**, temps **inclusif d’application**, **temps exclusif d’application**et **nombre d’appels**.

3. Sélectionnez **processus** dans la liste déroulante **affichage actuel** .

4. La vue processus affiche une table qui comprend l' **ID de processus**, le **nom de processus**, l’heure de **début**et l' **heure de fin**. Vous pouvez trier les données en cliquant sur les noms de colonnes.

## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : utilisation de la hiérarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
