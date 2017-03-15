---
title: "Options, &#201;diteur de texte, C#, Mise en forme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "mettre en forme (C#)"
  - "mettre en forme (J#)"
  - "Éditeur de texte (boîte de dialogue Options), mise en forme"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Options, &#201;diteur de texte, C#, Mise en forme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez la boîte de dialogue de page de propriétés **Mise en forme** pour définir des options de mise en forme du code dans l'éditeur de code.  Pour accéder à cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**, développez **Éditeur de texte**, développez **C\#**, puis cliquez sur **Mise en forme**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Paramètres généraux  
 Les paramètres généraux affectent la manière avec laquelle l'éditeur de code applique les options de mise en forme au code.  
  
## Liste UIElement  
  
|Étiquette|Description|  
|---------------|-----------------|  
|**Mise en forme automatique de l'instruction sur ;**|Lorsqu'elle est sélectionnée, cette option met en forme les instructions conformément aux options sélectionnées pour l'éditeur de code, dès la fin de l'instruction.  Désactivez cette case à cocher si vous ne souhaitez pas que l'éditeur de code modifie les instructions.|  
|**Mise en forme automatique du bloc terminé sur }**|Lorsqu'elle est sélectionnée, cette option met en forme les blocs de code conformément aux options sélectionnées pour l'éditeur de code, dès la fin du bloc de code.  Désactivez cette case à cocher si vous ne souhaitez pas que l'éditeur de code modifie les blocs de code.|  
|**Ajuster la mise en retrait lors du collage**|Lorsqu'elle est sélectionnée, cette option met en forme le texte collé dans l'éditeur de code conformément aux options sélectionnées dans l'éditeur de code.  Désactivez cette case à cocher si vous ne souhaitez pas que le texte collé soit modifié.|  
  
## Fenêtre Aperçu  
 Les volets d'options **Mise en retrait**, **Nouvelles lignes**, **Espacement** et **Enveloppement** offrent tous une fenêtre d'aperçu.  La fenêtre d'aperçu montre l'effet de chaque option.  Pour utiliser la fenêtre d'aperçu, sélectionnez une option de mise en forme.  La fenêtre d'aperçu montre un exemple de l'option sélectionnée.  Par exemple, modifier le paramètre, activer ou désactiver une case à cocher met à jour la fenêtre d'aperçu en affichant l'effet du nouveau paramètre.  
  
## Remarques  
 Les options de mise en retrait dans les pages **Tabulations** de chaque langage déterminent uniquement l'endroit où l'éditeur de code place le curseur lorsque vous appuyez sur ENTRÉE en fin de ligne.  Les options de mise en retrait sous **Mise en forme** s'appliquent lorsque le code est mis en forme automatiquement, par exemple, lorsque vous collez du code dans le fichier pendant que l'option **Ajuster la mise en retrait lors du collage** est sélectionnée, et lorsque le bloc qui est mis en forme est tapé manuellement.  
  
## Voir aussi  
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)