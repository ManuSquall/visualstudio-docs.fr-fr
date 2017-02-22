---
title: "Personnalisation des fen&#234;tres de Code &#224; l’aide de l’API h&#233;rit&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - code windows"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Personnalisation des fen&#234;tres de Code &#224; l’aide de l’API h&#233;rit&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une fenêtre de code est un objet de fenêtre de document qui prend en charge une ou plusieurs vues de texte. Les mêmes fonctionnalités d’une fenêtre de code dépendent du service de langage associé. En mode d’interface multidocument \(MDI\), la fenêtre de code est l’enfant MDI.  
  
 Fenêtres de code sont contrôlées par les services de langage, et chaque service de langage peut fournir son propre gestionnaire de fenêtres du code. Ainsi, le service de langage ajouter ses propres ornements dans la fenêtre de code, tels que les tildes, la colorisation et bien plus encore. Pour plus d’informations sur la création d’une fenêtre principale, consultez [L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Une fenêtre de code est un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui a une vue de texte et tous les ornements doit se trouver dans l’objet. Lorsque vous créez la fenêtre de code pendant votre instanciation de la base de l’éditeur, votre service de langage peut attacher un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> dans la fenêtre de code comme est indiqué dans l’illustration suivante.  
  
 ![Graphique CodeWindow](../extensibility/media/vscodewindow.png "vscodewindow")  
Fenêtre Code  
  
 Le service de langage implémente le Gestionnaire de fenêtres de code et est chargé de gérer les ornements, comme une barre de menu déroulant. La fenêtre de code appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode lors de l’initialisation de fenêtre de code. Lorsque cet appel est effectué, le service de langage peut ajouter une barre de menu déroulant ou une barre de boutons \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) dans la fenêtre de code.  
  
## Dans cette section  
 `Customizing Code Windows by Using the Legacy API`  
 Explique comment personnaliser des fenêtres de code à l’aide de l’API héritée.  
  
 [Comment : héberger un éditeur dans un autre éditeur](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explique comment héberger un second éditeur à l’intérieur d’une fenêtre d’éditeur.  
  
 [Comment : déclencher des événements lorsque l'éditeur perd le Focus](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explique comment associer une vue de document à un objet de données de document.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [L'accès à theText vue à l'aide de l'API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)