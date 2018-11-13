---
title: Options, Éditeur de texte, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 742d6394975b6920218579e1b4652bb2e99c479c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670778"
---
# <a name="options-text-editor-javascript-intellisense"></a>Options, Éditeur de texte, JavaScript, IntelliSense
Utilisez la page **IntelliSense** de la boîte de dialogue **Options** pour modifier les paramètres qui affectent le comportement d'IntelliSense pour JavaScript. Vous pouvez accéder à la page **IntelliSense** en choisissant **Outils** > **Options** dans la barre de menus, puis en développant **Éditeur de texte** > **JavaScript** > **IntelliSense**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

La page **IntelliSense** contient les sections suivantes :

## <a name="statement-completion"></a>Compléter automatiquement les instructions
 Vous pouvez utiliser ces options pour modifier le comportement de la saisie semi-automatique des instructions IntelliSense.

### <a name="uielement-list"></a>Liste des éléments d’interface
 **Utiliser uniquement la touche Tab ou Entrée pour valider**

 Quand vous cochez cette case, l’éditeur de code JavaScript ajoute des instructions avec les éléments sélectionnés dans la liste de complétion seulement quand vous appuyez sur la touche **Tab** ou **Entrée**. Quand vous décochez cette case, d’autres caractères, comme un point, une virgule, deux-points, une parenthèse ouvrante et une accolade ouvrante ({), peuvent également ajouter des instructions avec les éléments sélectionnés.

## <a name="references"></a>Références
 Vous pouvez utiliser ces options pour spécifier les types de fichiers IntelliSense .js qui sont dans la portée pour différents types de projet JavaScript. Les références IntelliSense sont généralement utilisées pour fournir une prise en charge IntelliSense pour les objets globaux. Vous pouvez également utiliser cette page pour définir l'ordre de chargement des scripts qui doivent être chargés au moment de l'exécution, et ajouter des fichiers d'extension IntelliSense.

### <a name="uielement-list"></a>Liste des éléments d’interface
 **Groupes de référence**

 Cette option spécifie le type de groupe de référence. Trois groupes de référence sont pris en charge :

 Vous pouvez utiliser les groupes de référence prédéfinis pour spécifier les fichiers IntelliSense .js particuliers qui sont dans la portée des projets JavaScript. Quatre groupes de référence sont disponibles :

- Implicite ( *version*de Windows) pour les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] en JavaScript. Les fichiers inclus dans ce groupe se trouvent dans la portée pour chaque fichier .js ouvert dans l’éditeur de code pour les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] utilisant JavaScript.

- Implicite (Web) pour les projets HTML5. Les fichiers inclus dans ce groupe figurent dans la portée de chaque fichier .js ouvert dans l'éditeur de code pour ces types de projet.

- Groupes de référence de processus de travail dédiés, pour les traitements web HTML5. Les fichiers spécifiés dans ce groupe figurent dans la portée des fichiers .js qui possèdent une référence explicite à un groupe de référence de processus de travail dédié.

- Générique pour les autres types de projet JavaScript.

**Fichiers inclus**

Cette option spécifie l'ordre dans lequel les fichiers sont chargés dans le contexte du service de langage. Vous pouvez configurer l'ordre à l'aide des boutons **Supprimer**, **Monter**et **Descendre** . Pour qu'IntelliSense fonctionne correctement, un fichier qui dépend des autres doit être chargé après l'autre fichier.

> [!CAUTION]
> Si un objet est défini de manière inconditionnelle dans deux références implicites ou plus, la dernière référence de cette liste sera utilisée pour définir l'objet.


**Ajouter une référence au groupe**

Cette option permet d'ajouter des fichiers IntelliSense .js supplémentaires en parcourant les fichiers appropriés.

**Télécharger les références distantes (par exemple, http://) pour les fichiers dans le projet Fichiers divers**

Quand cette case est cochée, et si vous avez un fichier JavaScript ouvert en dehors du contexte d’un projet, Visual Studio télécharge des fichiers JavaScript distants référencés dans le fichier pour fournir des informations IntelliSense. Si cette option est sélectionnée, les fichiers sont téléchargés lorsque vous les incluez comme référence dans votre fichier JavaScript.

> [!NOTE]
> Dans le cas des projets web, les fichiers distants auxquels ils font référence sont téléchargés par défaut.



## <a name="see-also"></a>Voir aussi

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)