---
title: Options des Outils R dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
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
ms.openlocfilehash: 9b680c73d54c9809e3f4c46dc2841f1f320e4af9
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---


# <a name="r-tools-for-visual-studio-options"></a>Options des Outils R dans Visual Studio
 
Les paramètres sont accessibles par l’intermédiaire du menu **Outils R > Options**, ou par l’intermédiaire d’**Outils > Options** et en faisant défiler la page jusqu’à **Outils R** :
 
  ![Boîte de dialogue Options pour les Outils R](~/docs/rtvs/media/options-dialog.png)

Les sections suivantes décrivent les différentes options disponibles dans cette page.

> [!Note]
> Quand vous accédez aux options par l’intermédiaire du menu général **Outils > Options**, vous devrez peut-être sélectionner la zone **Afficher tous les paramètres** en bas pour que la page **Outils R** s’affiche.

<a name="data-scientist-layout"</a>

Il existe également un élément de menu spécial **Outils R > Paramètres de science des données** qui configure l’IDE de Visual Studio avec une disposition optimisée pour les besoins des scientifiques des données. Plus précisément, cette option ouvre les fenêtres [Interactive](interactive-repl.md), [Explorateur de variables](variable-explorer.md) et [Espaces de travail](workspaces.md) :

![Disposition de fenêtre pour scientifique des données dans Visual Studio](~/docs/rtvs/media/installation-data-scientist-layout-result.png)

> [!Important]      
> Pour revenir ultérieurement à d’autres paramètres de Visual Studio, utilisez d’abord la commande **Outils > Importation et exportation de paramètres**, en sélectionnant **Exporter les paramètres d’environnement sélectionnés** et en spécifiant un nom de fichier. Pour restaurer ces paramètres, utilisez la même commande et sélectionnez **Importer les paramètres d’environnement sélectionnés**. Vous pouvez aussi utiliser les mêmes commandes si vous changez la disposition pour les scientifiques des données et que vous souhaitez y revenir plus tard, au lieu d’utiliser directement la commande **Paramètres de science des données**.

## <a name="debugging"></a>Débogage

Ces options contrôlent la façon dont les valeurs sont gérées dans l’[Explorateur de variables](variable-explorer.md) et dans les fenêtres d’outil de débogage comme Espion et Variables locales (voir [Débogage](debugging.md).

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Évaluer les liaisons actives | `True` | Quand cette option a la valeur `True`, vous voyez toujours la valeur de date la plus à jour lors de l’inspection des variables et des propriétés. Le risque est que l’évaluation des expressions peut avoir des effets secondaires, selon la façon dont elles ont été implémentées. |
| Afficher les variables préfixées par un point | `False` | Indique si les variables précédées de `.` sont affichées. |

## <a name="general"></a>Général

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Vérification des enquêtes/nouveautés | `Once a week` | Spécifie la fréquence à laquelle les Outils R doivent vérifier les mises à jour des enquêtes et nouveautés auprès du serveur. | 

## <a name="help"></a>Aide

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Navigateur web (F1) | `Internal` | Contrôle comment l’aide s’affiche quand vous recherchez un terme à l’aide de Ctrl+F1. Quand cette option a la valeur `Internal`, l’aide est affichée dans une fenêtre d’outil dans Visual Studio. Quand elle a la valeur `External`, l’aide est affichée dans votre navigateur par défaut. | 
| Chaîne de recherche web (F1) | `R site:stackoverflow.com` | Contrôle comment les termes de recherche sont transmis à votre moteur de recherche quand vous appuyez sur Ctrl+F1 sur un terme dans l’éditeur. Par défaut, la chaîne est `R site:stackoverflow.com`, ce qui ajoute `R` à votre terme de recherche. `site:stackoverflow.com` est une directive destinée au moteur de recherche, qui lui indique de limiter la recherche aux pages du domaine `stackoverflow.com`. | 
| Navigateur de l’aide R | `Automatic` | Contrôle comment l’aide s’affiche quand vous effectuez une recherche dans la documentation R à l’aide de Ctrl+F1, `?` ou `??`. Quand cette option a la valeur `Automatic`, l’aide s’affiche dans la fenêtre appropriée. Par exemple, l’aide HTML s’affiche dans une fenêtre d’outil Visual Studio, tandis que les fichiers PDF s’affichent dans votre programme PDF par défaut. Quand elle a la valeur `External`, l’aide s’affiche dans le navigateur web par défaut. |

## <a name="history"></a>Historique

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Toujours enregistrer l’historique | `True` | Détermine si RTVS écrit votre historique des commandes dans un fichier `.RHistory` dans votre répertoire de travail chaque fois que le projet est fermé. Notez que cela se produit même si vous n’enregistrez pas votre projet avant de quitter. |
| Réinitialiser le filtre de recherche | `True` | Détermine si la fenêtre Historique peut filtrer votre historique des commandes pour afficher uniquement les commandes qui correspondent au terme du filtre dans la boîte de dialogue Historique R. Ce paramètre détermine s’il faut réinitialiser votre filtre de recherche de l’historique chaque fois que vous exécutez une nouvelle commande, ou que vous basculez vers un nouveau projet, ce qui déclenche le chargement d’un autre fichier `.RHistory`. Le paramètre par défaut `True` évite d’être surpris quand vous exécutez une commande avec un filtre défini et que vous vous demandez pourquoi la commande que vous venez d’exécuter n’apparaît dans l’historique. |
| Utiliser la sélection multiligne | `True` | Spécifie si vous pouvez sélectionner une instruction sur plusieurs lignes dans l’historique avec un seul clic. Autorise également la navigation avec les flèches Haut/Bas dans les fenêtres Interactive par instructions plutôt que par lignes. |

## <a name="html"></a>HTML

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Navigateur de pages HTML | `External` | Détermine où est affiché le contenu tel qu’un tracé `ggvis` ou une application `shiny`. `Internal` affiche la sortie HTML dans une fenêtre d’outil dans Visual Studio. `External` affiche la sortie HTML dans votre navigateur par défaut. | 

## <a name="logging"></a>Journalisation

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Journaliser les événements | `Normal` | Contrôle le niveau de détail de la journalisation pour les diagnostics RTV. Le paramètre par défaut `Normal` crée un fichier journal dans votre répertoire `TEMP`. Quand cette option a la valeur `Traffic`, RTVS enregistre toutes les commandes et les réponses dans votre session. Ces fichiers journaux ne quittent jamais votre ordinateur, mais ils peuvent être utiles pour diagnostiquer des problèmes dans RTVS. |

## <a name="markdown"></a>Markdown

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Navigateur d’aperçu Markdown | `External` | Détermine où est affichée la sortie HTML RMarkdown. `Internal` affiche le document HTML RMarkdown dans une fenêtre d’outil dans Visual Studio. `External` affiche le HTML RMarkdown à l’aide de votre navigateur par défaut. | 

## <a name="r-engine"></a>Moteur R

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Page de codes | `(OS Default)` | Définit la page de codes (paramètres régionaux) pour R. Par défaut, les paramètres régionaux sous-jacents du système d’exploitation sont utilisés. | 
| Miroir CRAN | `(Use .Rprofile)` | Définit la mise en miroir CRAN par défaut pour les installations de packages. Le paramètre par défaut `Use .Rprofile` respecte les paramètres de miroir CRAN dans votre fichier `.RProfile`. Vous pouvez remplacer cette valeur en sélectionnant l’un des miroirs CRAN répertoriés dans la liste déroulante. |
| Répertoire de travail | dossier propre à l’utilisateur | Défini sur le répertoire de travail actuel, qui est généralement défini chaque fois qu’un projet est ouvert. |

## <a name="workspace"></a>Espace de travail

| Option | Valeur par défaut | Description | 
| --- | --- | --- |
| Charger l’espace de travail à l’ouverture du projet | `No` | `Yes` active le chargement des données de session à partir du fichier `.RData` dans l’environnement global à l’ouverture du projet. |
| Demander l’enregistrement de l’espace de travail en cas de réinitialisation | `Yes` | `No` désactive l’invite d’enregistrement de votre espace de travail quand vous cliquez sur le bouton Réinitialiser dans la fenêtre Interactive. |
| Enregistrer l’espace de travail à la fermeture du projet | `No` | `Yes` active l’enregistrement de l’environnement global dans le fichier `.RData` à la fermeture du projet. |
| Afficher la boîte de dialogue de confirmation avant de changer d’espace de travail | `Yes` | `No` désactive l’invite de confirmation lors du basculement entre différents espaces de travail. Voir [Basculement entre espaces de travail](workspaces.md#switching-between-workspaces). |
 
