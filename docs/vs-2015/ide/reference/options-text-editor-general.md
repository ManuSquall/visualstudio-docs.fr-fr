---
title: Options, Éditeur de texte, Général │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
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
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662264"
---
# <a name="options-text-editor-general"></a>Options, Éditeur de texte, Général
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de modifier les paramètres globaux de l’éditeur de code et de texte de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pour afficher cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**, développez le dossier **Éditeur de texte**, puis cliquez sur **Général**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Paramètres
 La modification du texte par glisser-déplacer lorsqu’elle est sélectionnée, vous permet de déplacer du texte en le sélectionnant et en le faisant glisser avec la souris vers un autre emplacement dans le document actif ou dans tout autre document ouvert.

 Mise en surbrillance automatique des délimiteurs quand ils sont sélectionnés, les caractères de délimitation qui séparent les paramètres ou les paires élément-valeur, ainsi que les accolades correspondantes sont mis en surbrillance

 Suivi des modifications lorsque l’éditeur de code est sélectionné, une ligne jaune verticale apparaît dans la marge de sélection pour marquer le code qui a changé depuis le dernier enregistrement du fichier. Quand vous enregistrez les modifications apportées, les lignes verticales deviennent vertes.

 Détection automatique de l’encodage UTF-8 sans signature par défaut, l’éditeur détecte l’encodage en recherchant des marques d’ordre d’octet ou des balises CharSet. Si l’éditeur de code ne trouve ni l’un ni l’autre dans le document actif, il tente de détecter automatiquement l’encodage UTF-8 en analysant les séquences d’octets. Pour désactiver la détection automatique de l’encodage, désactivez cette option.

## <a name="display"></a>Afficher
 Marge de sélection : lorsque cette option est sélectionnée, elle affiche une marge verticale le long du bord gauche de la zone de texte de l’éditeur. Vous pouvez cliquer dans cette marge pour sélectionner toute une ligne de texte, ou cliquer et faire glisser la souris pour sélectionner des lignes de texte consécutives.

|Marge de sélection activée|Marge de sélection désactivée|
|-------------------------|--------------------------|
|![Capture d’écran HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "|::ref1::|")|![Capture d’écran HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "|::ref2::|")|

 Marge des indicateurs : lorsque cette option est sélectionnée, une marge verticale s’affiche à l’extérieur du bord gauche de la zone de texte de l’éditeur. Quand vous cliquez dans cette marge, une icône et une info-bulle relatives au texte s’affichent. Par exemple, les raccourcis des points d’arrêt ou de la liste des tâches s’affichent dans la marge des indicateurs. Le contenu de la marge des indicateurs ne s’imprime pas.

 Barre de défilement verticale quand elle est sélectionnée, affiche une barre de défilement verticale qui vous permet de faire défiler vers le haut et vers le haut pour afficher les éléments qui se trouvent en dehors de la zone d’affichage de l’éditeur. Si des barres de défilement verticales ne sont pas disponibles, vous pouvez faire défiler le contenu de l’éditeur à l’aide des touches du curseur et des touches Page précédente et Page suivante.

 Barre de défilement horizontale : lorsque cette option est sélectionnée, elle affiche une barre de défilement horizontale qui vous permet de faire défiler d’un côté à l’autre pour afficher les éléments qui se trouvent en dehors de la zone d’affichage de l’éditeur. Si les barres de défilement horizontales ne sont pas disponibles, vous pouvez faire défiler le contenu de l’éditeur à l’aide des touches du curseur.

 Mettre en surbrillance la ligne active quand elle est sélectionnée, affiche une zone grise autour de la ligne de code où se trouve le curseur.

## <a name="see-also"></a>Voir aussi
 [Options, éditeur de texte, toutes les langues](../../ide/reference/options-text-editor-all-languages.md) [options, éditeur de texte, tous les langages, options onglets](../../ide/reference/options-text-editor-all-languages-tabs.md) [, éditeur de texte, extension](../../ide/reference/options-text-editor-file-extension.md) [de fichier identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [Personnalisation de l’éditeur](../../ide/customizing-the-editor.md) [à l’aide de IntelliSense](../../ide/using-intellisense.md)
