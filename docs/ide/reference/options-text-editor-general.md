---
title: Options, Éditeur de texte, Général
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed55d65555425b04749696b5510cfe799d2a1194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80472824"
---
# <a name="options-dialog-box-text-editor--general"></a>Boîte de dialogue Options : éditeur de texte \> général

Cette boîte de dialogue vous permet de modifier les paramètres globaux de l’éditeur de code et de texte de Visual Studio. Pour afficher cette boîte de dialogue, sélectionnez **Options** dans le menu **Outils**, développez le dossier **Éditeur de texte**, puis sélectionnez **Général**.

## <a name="settings"></a>Paramètres

### <a name="drag-and-drop-text-editing"></a>Éditer le texte par glisser-déplacer

Quand elle est sélectionnée, cette option vous permet de déplacer du texte en le sélectionnant et en le faisant glisser avec la souris jusqu’à un autre emplacement au sein du document actif ou de tout document ouvert.

### <a name="automatic-delimiter-highlighting"></a>Mettre automatiquement les délimiteurs en surbrillance

Quand cette option est sélectionnée, les délimiteurs qui séparent les paramètres ou les paires élément-valeur, ainsi que les accolades correspondantes, sont mis en surbrillance.

### <a name="track-changes"></a>Suivre les modifications

Quand l’éditeur de code est sélectionné, une ligne jaune verticale apparaît dans la marge de sélection pour marquer le code qui a changé depuis le dernier enregistrement du fichier. Quand vous enregistrez les modifications apportées, les lignes verticales deviennent vertes.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Détecter automatiquement le codage UTF-8 sans signature

Par défaut, l’éditeur détecte l’encodage en recherchant les marques d’ordre d’octet ou les balises de jeu de caractères. Si l’éditeur de code ne trouve ni l’un ni l’autre dans le document actif, il tente de détecter automatiquement l’encodage UTF-8 en analysant les séquences d’octets. Pour désactiver la détection automatique de l’encodage, désactivez cette option.

### <a name="follow-project-coding-conventions"></a>Suivre les conventions de codage du projet

Quand cette option est sélectionnée, les conventions de codage spécifiées du projet remplacent toutes les conventions de codage que vous utilisez dans vos projets personnels.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Activer le clic de souris pour exécuter Atteindre la définition

Quand cette option est sélectionnée, vous pouvez appuyer sur **Ctrl** et pointer sur un élément tout en cliquant sur la souris. Cela vous permet d’atteindre la définition de l’élément sélectionné. Vous pouvez également choisir **Alt** ou **Ctrl** + **Alt** dans la liste déroulante **Utiliser la touche de modification**.

Cochez la case **Ouvrir la définition dans l’aperçu** pour afficher la définition de l’élément dans une fenêtre sans être obligé de quitter votre emplacement actuel dans l’éditeur de code.

## <a name="display"></a>Afficher

### <a name="selection-margin"></a>Marge de sélection

Quand cette option est sélectionnée, une marge verticale s’affiche le long du bord gauche de la zone de texte de l’éditeur. Vous pouvez cliquer dans cette marge pour sélectionner toute une ligne de texte, ou cliquer et faire glisser la souris pour sélectionner des lignes de texte consécutives.

|Marge de sélection activée|Marge de sélection désactivée|
| - | - |
|![Capture d'écran HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Capture d'écran HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Marge des indicateurs

Quand cette option est sélectionnée, une marge verticale s’affiche à l’extérieur du bord gauche de la zone de texte de l’éditeur. Quand vous cliquez dans cette marge, une icône et une info-bulle relatives au texte s’affichent. Par exemple, les raccourcis des points d’arrêt ou de la liste des tâches s’affichent dans la marge des indicateurs. Le contenu de la marge des indicateurs ne s’imprime pas.

### <a name="highlight-current-line"></a>Mettre en surbrillance la ligne active

Quand elle est sélectionnée, cette option affiche une zone grise autour de la ligne de code dans laquelle le curseur.

### <a name="show-structure-guide-lines"></a>Afficher les lignes de repère de structure

Quand cette option est sélectionnée, des lignes verticales alignées avec les blocs de code structurés sont affichées dans l’éditeur, ce qui vous permet d’identifier facilement les différents blocs de code.

### <a name="show-file-health-indicator"></a>Afficher l’indicateur d’intégrité du fichier

Lorsque cette option est sélectionnée, une barre d’état des indicateurs d’intégrité de fichier (erreurs, avertissements), avec les options de nettoyage du code, s’affiche dans le coin inférieur gauche de l’éditeur.

## <a name="see-also"></a>Voir aussi

- [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)
- [Options, Éditeur de texte, Tous les langages, Tabulations](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Options, Éditeur de texte, Extension de fichier](../../ide/reference/options-text-editor-file-extension.md)
- [Identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Personnalisation de l’éditeur](../how-to-change-text-case-in-the-editor.md)
- [Utilisation d’IntelliSense](../../ide/using-intellisense.md)
