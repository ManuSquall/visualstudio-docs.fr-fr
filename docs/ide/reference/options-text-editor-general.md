---
title: "Options, &#201;diteur de texte, G&#233;n&#233;ral | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "éditeur de texte (boîte de dialogue Options)"
  - "Éditeur de code"
  - "Éditeur de texte (Visual Studio)"
  - "éditeurs, paramètres globaux"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Options, &#201;diteur de texte, G&#233;n&#233;ral
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de modifier les paramètres globaux de l'éditeur de code\/texte de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Pour afficher cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**, développez le nœud **Éditeur de texte**, puis cliquez sur **Général**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d’informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Paramètres  
 Éditer le texte par glisser\-déplacer  
 Lorsque cette case à cocher est activée, elle vous permet de déplacer du texte en le sélectionnant et en le faisant glisser avec la souris jusqu'à un autre emplacement, au sein du document en cours ou de tout document ouvert.  
  
 Mettre automatiquement les délimiteurs en surbrillance  
 En cas de sélection, les délimiteurs qui séparent les paramètres ou les paires élément\-valeur, ainsi que les accolades correspondantes, sont mis en surbrillance.  
  
 Suivre les modifications  
 Lorsque l'éditeur de code est sélectionné, une ligne jaune verticale apparaît dans la marge de sélection marquer le code qui a changé depuis que le fichier a été récemment enregistrée.  Lorsque vous enregistrez les modifications, les lignes verticales sont vertes.  
  
 Détecter automatiquement l'encodage UTF\-8 sans signature  
 Par défaut, l'éditeur détecte l'encodage en recherchant les marques d'ordre d'octet ou les balises de jeu de caractères.  Si l'éditeur de code ne trouve ni l'un ni l'autre dans le document en cours, l'éditeur de code essaie de détecter automatiquement l'encodage UTF\-8 en analysant les séquences d'octets.  Pour désactiver la détection automatique de l'encodage, désactivez cette option.  
  
## Affichage  
 Marge de sélection  
 Lorsque cette case à cocher est activée, une marge verticale s'affiche le long du bord gauche de la zone de texte de l'éditeur.  Vous pouvez cliquer dans cette marge pour sélectionner toute une ligne de texte, ou cliquer et sélectionner des lignes de texte consécutives en faisant glisser la souris.  
  
|Marge de sélection activée|Marge de sélection désactivée|  
|--------------------------------|-----------------------------------|  
|![Capture d'écran HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![Capture d'écran HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.png "vxSelmaroff")|  
  
 Marge des indicateurs  
 Lorsque cette case à cocher est activée, une marge verticale s'affiche à l'extérieur du bord gauche de la zone de texte de l'éditeur.  Si vous cliquez dans la marge, une icône et une info\-bulle relatives au texte s'affichent.  Par exemple, les raccourcis des points d'arrêt ou d'une liste de tâches s'affichent dans la marge des indicateurs.  Le contenu de la marge des indicateurs ne s'imprime pas.  
  
 Barre de défilement verticale  
 Lorsque cette case à cocher est activée, une barre de défilement verticale s'affiche pour vous permettre de faire défiler verticalement les éléments situés hors de la zone d'affichage de l'Éditeur.  Si des barres de défilement verticales ne sont pas disponibles, vous pouvez faire défiler le contenu de l'Éditeur à l'aide des touches du curseur et des touches Page Précédente et Page Suivante.  
  
 Barre de défilement horizontale  
 Lorsque cette case à cocher est activée, une barre de défilement horizontale s'affiche pour vous permettre de faire défiler horizontalement les éléments situés hors de la zone d'affichage de l'Éditeur.  Si des barres de défilement horizontales ne sont pas disponibles, vous pouvez faire défiler le contenu de l'Éditeur à l'aide des touches du curseur.  
  
 Ligne active en surbrillance  
 Une fois sélectionné, affiche une zone grise autour de la ligne de code dans lequel le curseur se trouve.  
  
## Voir aussi  
 [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)   
 [Options, Éditeur de texte, Tous les langages, Onglets](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Options, Éditeur de texte, Extension de fichier](../../ide/reference/options-text-editor-file-extension.md)   
 [Identification et personnalisation des raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Personnalisation de l'éditeur](../../ide/customizing-the-editor.md)   
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)