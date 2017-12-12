---
title: "Options, Éditeur de texte, JavaScript, IntelliSense | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e18791f33ddb9c373af8b0af8def615c26374b3
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="options-text-editor-javascript-intellisense"></a>Options, Éditeur de texte, JavaScript, IntelliSense
Utilisez la page **IntelliSense** de la boîte de dialogue **Options** pour modifier les paramètres qui affectent le comportement d'IntelliSense pour JavaScript. Vous pouvez accéder à la page **IntelliSense** en choisissant **Outils**, **Options** dans la barre de menus, et en développant ensuite **Éditeur de texte**, **JavaScript**, **IntelliSense.**  
  
[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
La page **IntelliSense** contient les sections suivantes :  
  
## <a name="validation"></a>Validation  
 Vous pouvez utiliser ces options pour définir comment l'éditeur JavaScript doit valider la syntaxe dans votre document.  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Afficher les erreurs de syntaxe**  
 Lorsque cette case à cocher n'est pas activée, l'éditeur de code JavaScript n'affiche aucune erreur de syntaxe. Cela est utile si vous travaillez avec du code dont vous n'êtes pas l'auteur et que vous n'avez pas l'intention de corriger les erreurs de syntaxe.  
  
 Lorsque cette case à cocher est activée, vous pouvez activer la case à cocher **Afficher les erreurs comme des avertissements** .  
  
 **Afficher les erreurs comme des avertissements**  
 Lorsque cette case à cocher est activée, les erreurs JavaScript sont indiquées sous forme d'avertissements et non d'erreurs dans la liste d'erreurs.  
  
 **Télécharger les références distantes (par exemple, http://) pour les fichiers dans le projet Fichiers divers**  
 Lorsque cette case à cocher est activée, et si vous disposez d'un fichier JavaScript ouvert en dehors d'un projet, Visual Studio télécharge des fichiers JavaScript distants référencés dans le fichier afin de fournir des informations IntelliSense. Si cette option est sélectionnée, les fichiers sont téléchargés lorsque vous les incluez en tant que référence dans votre fichier JavaScript.  
  
> [!NOTE]
>  Pour les projets Web, les fichiers distants référencés dans votre projet sont téléchargés par défaut.  
  
## <a name="statement-completion"></a>Compléter automatiquement les instructions  
 Vous pouvez utiliser ces options pour modifier le comportement de la saisie semi-automatique des instructions IntelliSense.  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Utiliser uniquement la touche Tabulation ou Entrée pour valider**  
 Lorsque cette case à cocher est activée, l'éditeur de code JavaScript ajoute des instructions aux éléments sélectionnés dans la liste de saisie semi-automatique uniquement lorsque vous appuyez sur la touche Tabulation ou la touche Entrée. Lorsque cette case à cocher est désactivée, d'autres caractères, comme un point, une virgule, deux-points, une parenthèse ouvrante, et une accolade ouvrante ({)) peuvent également ajouter des instructions aux éléments sélectionnés.  
  
## <a name="references"></a>Références  
 Vous pouvez utiliser ces options pour spécifier les types de fichiers IntelliSense .js qui sont dans la portée pour différents types de projet JavaScript. Les références IntelliSense sont généralement utilisées pour fournir une prise en charge IntelliSense pour les objets globaux. Vous pouvez également utiliser cette page pour définir l'ordre de chargement des scripts qui doivent être chargés au moment de l'exécution, et ajouter des fichiers d'extension IntelliSense.  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Groupes de référence**  
 Cette option spécifie le type de groupe de référence. Trois groupes de référence sont pris en charge :  
  
 Vous pouvez utiliser les groupes de référence prédéfinis pour spécifier les fichiers IntelliSense .js particuliers qui sont dans la portée des projets JavaScript. Quatre groupes de référence sont disponibles :  
  
-   Implicite ( *version*de Windows) pour les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] en JavaScript. Les fichiers inclus dans ce groupe se trouvent dans la portée pour chaque fichier .js ouvert dans l'éditeur de code pour les applications [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] utilisant JavaScript.  
  
-   Implicite (Web) pour les projets HTML5. Les fichiers inclus dans ce groupe figurent dans la portée de chaque fichier .js ouvert dans l'éditeur de code pour ces types de projet.  
  
-   Groupes de référence de processus de travail dédié pour les traitements Web HTML5. Les fichiers spécifiés dans ce groupe figurent dans la portée des fichiers .js qui possèdent une référence explicite à un groupe de référence de processus de travail dédié.  
  
-   Générique pour les autres types de projet JavaScript.  
  
**Fichiers inclus**  
Cette option spécifie l'ordre dans lequel les fichiers sont chargés dans le contexte du service de langage. Vous pouvez configurer l'ordre à l'aide des boutons **Supprimer**, **Monter**et **Descendre** . Pour qu'IntelliSense fonctionne correctement, un fichier qui dépend des autres doit être chargé après l'autre fichier.  
  
> [!CAUTION]
>  Si un objet est défini de manière inconditionnelle dans deux références implicites ou plus, la dernière référence de cette liste sera utilisée pour définir l'objet.  
  
**Ajouter une référence au groupe**  
Cette option permet d'ajouter des fichiers IntelliSense .js supplémentaires en parcourant les fichiers appropriés.  
  
## <a name="see-also"></a>Voir aussi  
[JavaScript IntelliSense](../../ide/javascript-intellisense.md)