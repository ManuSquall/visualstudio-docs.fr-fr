---
title: Fenêtre Liste d'erreurs
description: Découvrez la fenêtre de Liste d’erreurs et comment l’utiliser pour effectuer des tâches liées à la résolution des erreurs qu’elle affiche.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90d3f8f95cb4b6aef3b2538a26226f5bad40f33b
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924940"
---
# <a name="error-list-window"></a>Fenêtre Liste d'erreurs

> [!NOTE]
> La **liste d’erreurs** affiche des informations sur un message d’erreur spécifique. Vous pouvez copier le numéro d’erreur ou le texte de la chaîne d'erreur dans la fenêtre **Sortie**. Pour afficher la fenêtre **Sortie**, appuyez sur **Ctrl**+**Alt**+**O**. Consultez [Sortie, fenêtre](../../ide/reference/output-window.md).

La fenêtre **Liste d’erreurs** vous permet d’effectuer les tâches suivantes :

- afficher les erreurs, avertissements et messages générés pendant l'écriture du code ;

- rechercher les erreurs de syntaxe relevées par IntelliSense ;

- rechercher les erreurs de déploiement, certaines erreurs d'analyse statique et les erreurs détectées lors de l'application de stratégies de modèle d'entreprise ;

- double-cliquer sur toute entrée de message d'erreur pour ouvrir le fichier où le problème se produit et accéder à l'emplacement de l'erreur ;

- filtrer les entrées qui sont affichées et les colonnes d'information qui apparaissent pour chaque entrée ;

- rechercher des termes spécifiques et limiter la recherche au projet ou au document actif.

Pour afficher les **liste d’erreurs**, choisissez **Afficher** les  >  **liste d’erreurs** ou appuyez sur **CTRL** + **\\** + **E**.

Vous pouvez choisir les onglets **Erreurs**, **Avertissements** et **Messages** pour afficher les différents niveaux d’informations.

Pour trier la liste, cliquez sur n'importe quel en-tête de colonne. Pour trier à nouveau sur une colonne supplémentaire, maintenez la touche **Maj** enfoncée et cliquez sur un autre en-tête de colonne. Pour sélectionner les colonnes qui doivent être affichées et celles qui doivent être masquées, choisissez **Afficher les colonnes** dans le menu contextuel. Pour modifier l'ordre dans lequel les colonnes sont affichées, faites glisser les en-têtes de votre choix vers la droite ou la gauche.

## <a name="error-list-filters"></a>Filtres de la liste d'erreurs

Il existe deux types de filtre dans deux zones de liste déroulante, l’un à droite de la barre d’outils, et l’autre à gauche de la barre d’outils. La liste déroulante située à gauche de la barre d’outils spécifie l’ensemble de fichiers de code à utiliser (**Solution complète**, **Documents ouverts**, **Projet actif**, **Document actif**).

Vous pouvez restreindre la portée de la recherche pour analyser et agir sur des groupes d'erreurs. Par exemple, vous pouvez vous concentrer sur les erreurs principales qui empêchent la compilation d'un projet. Les options de portée disponibles sont les suivantes :

1. **Documents ouverts** : afficher les erreurs, les avertissements et les messages relatifs aux documents ouverts.

2. **Projet actif** : afficher les erreurs, les avertissements et les messages du projet du document actuellement sélectionné dans l’**Éditeur** ou du projet sélectionné dans l’**Explorateur de solutions**.

    > [!NOTE]
    > La liste filtrée d’erreurs, d’avertissements et de messages est modifiée si le projet du document actuellement sélectionné est différent du projet sélectionné dans l’**Explorateur de solutions**.

3. **Document actif** : afficher les erreurs, les avertissements et les messages du document actuellement sélectionné dans l’**Éditeur** ou dans l’**Explorateur de solutions**.

Si un filtre est actuellement appliqué aux résultats de la recherche, le nom du filtre apparaît dans la barre de titre **Liste d’erreurs**. Les boutons **Erreurs**, **Avertissements** et **Messages** affichent alors le nombre d’éléments filtrés affichés, ainsi que le nombre total d’éléments. Par exemple, les boutons indiquent « x erreurs sur y ». Si aucun filtre n’est appliqué, la barre de titre indique uniquement « Liste d’erreurs ».

La liste située à droite de la barre d'outils indique si les erreurs doivent être affichées à partir de la build (erreurs résultant d'une opération de build) ou à partir d'IntelliSense (erreurs détectées avant d'exécuter une build), ou les deux.

## <a name="search"></a>Recherche

Utilisez la zone de texte **Rechercher dans la liste des erreurs** située à droite de la barre d’outils **Liste d’erreurs** pour rechercher des erreurs spécifiques dans la liste d’erreurs. Vous pouvez rechercher sur toute colonne visible dans la liste et les résultats de la recherche sont toujours triés selon la colonne de tri prioritaire au lieu de la requête ou du filtre appliqué. Si vous choisissez la touche **Échap** tandis que le focus est dans la **Liste d’erreurs**, vous pouvez effacer le terme de recherche et les résultats de la recherche filtrés. Vous pouvez également cliquer sur la croix (**X**) à droite de la zone de texte pour l’effacer.

## <a name="save"></a>Enregistrer

Vous pouvez copier la liste d'erreurs et l'enregistrer dans un fichier. Sélectionnez les erreurs que vous voulez copier, cliquez avec le bouton droit sur la sélection, puis, dans le menu contextuel, sélectionnez **Copier**. Vous pouvez ensuite coller les erreurs dans un fichier. Si vous collez les erreurs dans une feuille de calcul Excel, les champs apparaissent comme colonnes individuelles.

## <a name="ui-element-list"></a>Liste des éléments de l'interface utilisateur

severity

Affiche les différents types d’entrée de la **Liste d’erreurs** (**Erreur**, **Message**, **Avertissement**, **Avertissement (actif)**, **Avertissement (inactif)**).

Code

Affiche le code d'erreur.

Description

Affiche le texte de l'entrée.

Project

Affiche le nom du projet actif.

Fichier

Affiche le nom de fichier.

Courbes

Affiche la ligne où apparaît le problème.
