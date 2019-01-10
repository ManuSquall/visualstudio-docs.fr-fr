---
title: Options, Éditeur de texte, Général
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdd4e366451dd81738305893727554e8b07ffb04
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871328"
---
# <a name="options-text-editor-general"></a>Options, Éditeur de texte, Général

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

## <a name="display"></a>Affichage

### <a name="selection-margin"></a>Marge de sélection

Quand cette option est sélectionnée, une marge verticale s’affiche le long du bord gauche de la zone de texte de l’éditeur. Vous pouvez cliquer dans cette marge pour sélectionner toute une ligne de texte, ou cliquer et faire glisser la souris pour sélectionner des lignes de texte consécutives.

|Marge de sélection activée|Marge de sélection désactivée|
| - | - |
|![Capture d'écran HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Capture d'écran HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Marge des indicateurs

Quand cette option est sélectionnée, une marge verticale s’affiche à l’extérieur du bord gauche de la zone de texte de l’éditeur. Quand vous cliquez dans cette marge, une icône et une info-bulle relatives au texte s’affichent. Par exemple, les raccourcis des points d’arrêt ou de la liste des tâches s’affichent dans la marge des indicateurs. Le contenu de la marge des indicateurs ne s’imprime pas.

### <a name="highlight-current-line"></a>Mettre en surbrillance la ligne active

Quand elle est sélectionnée, cette option affiche une zone grise autour de la ligne de code dans laquelle le curseur.

## <a name="see-also"></a>Voir aussi

- [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)
- [Options, Éditeur de texte, Tous les langages, Onglets](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Options, Éditeur de texte, Extension de fichier](../../ide/reference/options-text-editor-file-extension.md)
- [Identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Personnalisation de l’éditeur](../../ide/customizing-the-editor.md)
- [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)