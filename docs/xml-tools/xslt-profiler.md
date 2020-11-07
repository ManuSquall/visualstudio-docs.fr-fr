---
title: Performances XSLT
description: En savoir plus sur le profileur XSLT dans Visual Studio qui crée des rapports détaillés sur les performances XSLT pour vous aider à optimiser les performances de votre code XSLT.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4fd10df6a5cd91866633a46e1a512e91da2040
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351412"
---
# <a name="the-xslt-profiler"></a>Profileur XSLT

Le Générateur de profils XSLT crée des rapports de performances XSLT détaillés qui vous permettent de mesurer, d'évaluer et de cibler les problèmes liés aux performances dans le code XSLT. Le Générateur de profils XSLT inclut des conseils utiles pour les optimisations de feuille de style XSL et XSLT. Pour les applications XSLT qui demandent des performances maximales, cet outil peut être essentiel.

Le profileur XSLT fait partie de Visual Studio et est disponible dans le menu **XML** .

![Profileur XSLT](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> Le profileur XSLT est uniquement disponible dans l’édition Enterprise de Visual Studio.

## <a name="create-a-performance-report"></a>Créer un rapport de performances

1. Ouvrez un document XSLT dans Visual Studio.

2. Dans la barre de menus, choisissez **XML**  >  **Profile XSLT**.

3. Fournissez un document XML d'entrée. Si un document XML n'est pas déjà ouvert, vous êtes invité à entrer le fichier.

   L'analyse démarre, et une barre de progression affiche la progression dans l'éditeur. La sortie XSLT est également visible.

4. Une fois la session de performance terminée, vérifiez le rapport de performances pour analyser les performances de XSLT.

## <a name="get-all-available-views"></a>Obtient toutes les vues disponibles

1. Cliquez sur la liste déroulante **affichage actuel** pour obtenir toutes les vues disponibles.

2. Sélectionnez l’option **vue Résumé** dans la liste déroulante **affichage actuel** . Par défaut, un rapport de performances est affiché dans la **vue Résumé**. Cette vue sert de point de départ pour déterminer les problèmes de performances avec les documents XSLT. Le **mode Résumé** répertorie les points de données suivants :

   - Majorité des fonctions appelées

   - Fonctions faisant le plus de travail individuel

   - Fonctions les plus longues à exécuter

   Par défaut, il y a trois colonnes pour chaque point de données : le nom de la fonction, le nombre d'appels en valeur absolue, et une valeur en pourcentage de la fonction nommée par rapport au nombre total d'appels de fonction. À partir de chaque point de données dans la **vue Résumé** , vous pouvez accéder à des vues plus détaillées en cliquant avec le bouton droit sur les points de données de la fonction.

3. Sélectionnez l’option **affichage des fonctions** dans la liste déroulante **affichage actuel** . La **vue fonction** répertorie les fonctions appelées lors du profilage. Vous pouvez trier les données en cliquant sur un nom de colonne. Les colonnes affichées par défaut sont les suivantes :

    - **Nom de la fonction**

    - **Temps inclusif écoulé**

    - **Temps exclusif écoulé**

    - **Temps inclusif d’application**

    - **Temps exclusif d’application**

    - **Nombre d’appels**

   Toutes les colonnes d'heure sont affichées en valeurs absolues et en pourcentages. Le terme **exclusive** fait référence au temps total passé par une fonction à exécuter un temps d’exécution exclusif passé par d’autres fonctions appelées pendant l’exécution de cette fonction.

   Le terme **inclus** fait référence à la durée totale d’exécution d’une fonction, y compris la durée d’exécution de toutes les fonctions qu’elle a appelées et si l’une de ces fonctions appelées est appelée autres fonctions.

## <a name="select-callercallee-view"></a>Sélectionner la vue Appelant/Appelé

Sélectionnez la vue **appelant/appelé** dans la liste déroulante **affichage actuel** . La vue **appelant/appelé** comprend les trois parties distinctes suivantes :

- **Fonctions qui ont appelé** : toutes les fonctions qui ont appelé une fonction particulière sont répertoriées dans la partie supérieure de la vue.

- **Fonction active** : la fonction particulière qui a été appelée est indiquée dans la partie centrale de la vue.

- **Fonctions qui ont été appelées par** : toutes les fonctions qui ont été appelées par la fonction particulière sont répertoriées dans la partie inférieure de la vue.

Si une fonction nommée `SyncToNavigator` apparaît dans la partie centrale de la vue, toutes les fonctions qui ont appelé la fonction `SyncToNavigator` s'affichent dans la partie supérieure de la vue et toutes les fonctions appelées par la fonction `SyncToNavigator` s'affichent dans la partie inférieure de la vue.

- Vous pouvez modifier la fonction dans la partie centrale de la vue en double-cliquant sur une des fonctions répertoriées dans les autres parties de la vue. La vue est mise à jour automatiquement pour refléter les modifications.

- Vous pouvez aussi trier les données en cliquant sur les noms de colonnes.

## <a name="select-call-tree-view"></a>Sélectionner la vue de l’arborescence des appels

- Sélectionnez **vue arborescence des appels** dans la liste déroulante **affichage actuel** . Cette vue est une arborescence de l’exécution du programme.

   La **vue arborescence des appels** affiche la racine de l’arborescence en tant que nom de processus. Les fonctions sont les nœuds de l'arborescence. Cette vue vous permet d'explorer des traces d'appels spécifiques et d'analyser les traces qui affectent le plus les performances. La vue est similaire à la **vue** de la pile des appels disponible pendant le débogage. En plus des colonnes de l' **affichage des fonctions** , dans la **vue arborescence des appels** , il existe une colonne supplémentaire pour afficher le nom du **module**.

- Sélectionnez **marques** dans la liste déroulante **affichage actuel** .

   Avec le profileur XSLT, il existe des marques qui s’affichent dans le flux de collecte de données avec un commentaire associé. Les marques sont emplacements dans le code qui ont des compteurs. Lorsque vous indiquez au Générateur de profils SLT de collecter des compteurs de performance XSLT, ceux-ci sont collectés chaque fois que l'une de ces marques est exécutée. Les données sont affichées dans un tableau contenant l' **ID de marque** , le **nom de marque** ( **programme de démarrage** , le **programme final** ) et l' **horodatage**. Les marques ne sont pas agrégées et apparaissent dans l’ordre chronologique dans la **vue marques** du rapport de performances.

## <a name="select-modules-in-the-current-view"></a>Sélectionner des modules dans l'affichage actuel

- Sélectionnez **modules** dans la liste déroulante **affichage actuel** .

   La vue de modules est une liste plate de toutes les fonctions agrégées au niveau du module. Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module. Vous pouvez trier les données en cliquant sur un nom de colonne. Par défaut, il existe à la fois des valeurs absolues et des nombres de pourcentages pour le **temps inclusif écoulé** , temps **exclusif écoulé** , temps **inclusif d’application** , **temps exclusif d’application** et **nombre d’appels**.

- Sélectionnez **processus** dans la liste déroulante **affichage actuel** .

   La vue processus affiche une table qui comprend l' **ID de processus** , le **nom de processus** , l’heure de **début** et l' **heure de fin**. Vous pouvez trier les données en cliquant sur les noms de colonnes.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : utilisation de la hiérarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
