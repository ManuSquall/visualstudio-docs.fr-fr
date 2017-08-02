---
title: "Options, Éditeur de texte, Général │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 29
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: eee3b34e9f473c200463b65f1b839416f5dce0ec
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-general"></a>Options, Éditeur de texte, Général
Cette boîte de dialogue vous permet de modifier les paramètres globaux de l’éditeur de code et de texte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour afficher cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**, développez le dossier **Éditeur de texte**, puis cliquez sur **Général**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="settings"></a>Paramètres  
 Éditer le texte par glisser-déplacer  
 Quand elle est sélectionnée, cette option vous permet de déplacer du texte en le sélectionnant et en le faisant glisser avec la souris jusqu’à un autre emplacement au sein du document actif ou de tout document ouvert.  
  
 Mettre automatiquement les délimiteurs en surbrillance  
 Quand cette option est sélectionnée, les délimiteurs qui séparent les paramètres ou les paires élément-valeur, ainsi que les accolades correspondantes, sont mis en surbrillance.  
  
 Suivre les modifications  
 Quand l’éditeur de code est sélectionné, une ligne jaune verticale apparaît dans la marge de sélection pour marquer le code qui a changé depuis le dernier enregistrement du fichier. Quand vous enregistrez les modifications apportées, les lignes verticales deviennent vertes.  
  
 Détecter automatiquement le codage UTF-8 sans signature  
 Par défaut, l’éditeur détecte l’encodage en recherchant les marques d’ordre d’octet ou les balises de jeu de caractères. Si l’éditeur de code ne trouve ni l’un ni l’autre dans le document actif, il tente de détecter automatiquement l’encodage UTF-8 en analysant les séquences d’octets. Pour désactiver la détection automatique de l’encodage, désactivez cette option.  
  
## <a name="display"></a>Affichage  
 Marge de sélection  
 Quand cette option est sélectionnée, une marge verticale s’affiche le long du bord gauche de la zone de texte de l’éditeur. Vous pouvez cliquer dans cette marge pour sélectionner toute une ligne de texte, ou cliquer et faire glisser la souris pour sélectionner des lignes de texte consécutives.  
  
|Marge de sélection activée|Marge de sélection désactivée|  
|-------------------------|--------------------------|  
|![Capture d’écran HTMLpageSelectionMarginOn](~/ide/reference/media/vxselmaron.gif "vxSelmaron")|![Capture d’écran HTMLpageSelectionMarginOff](~/ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Marge des indicateurs  
 Quand cette option est sélectionnée, une marge verticale s’affiche à l’extérieur du bord gauche de la zone de texte de l’éditeur. Quand vous cliquez dans cette marge, une icône et une info-bulle relatives au texte s’affichent. Par exemple, les raccourcis des points d’arrêt ou de la liste des tâches s’affichent dans la marge des indicateurs. Le contenu de la marge des indicateurs ne s’imprime pas.  
  
 Barre de défilement verticale  
 Quand cette option est sélectionnée, une barre de défilement verticale s’affiche pour vous permettre de faire défiler verticalement les éléments situés hors de la zone d’affichage de l’éditeur. Si des barres de défilement verticales ne sont pas disponibles, vous pouvez faire défiler le contenu de l’éditeur à l’aide des touches du curseur et des touches Page précédente et Page suivante.  
  
 Barre de défilement horizontale  
 Quand cette option est sélectionnée, une barre de défilement horizontale s’affiche pour vous permettre de faire défiler horizontalement les éléments situés hors de la zone d’affichage de l’éditeur. Si les barres de défilement horizontales ne sont pas disponibles, vous pouvez faire défiler le contenu de l’éditeur à l’aide des touches du curseur.  
  
 Mettre en surbrillance la ligne active  
 Quand elle est sélectionnée, cette option affiche une zone grise autour de la ligne de code dans laquelle le curseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)   
 [Options, Éditeur de texte, Tous les langages, Tabulations](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Options, Éditeur de texte, Extension de fichier](../../ide/reference/options-text-editor-file-extension.md)   
 [Identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Personnalisation de l’éditeur](../../ide/customizing-the-editor.md)   
 [Utilisation d’IntelliSense](../../ide/using-intellisense.md)
