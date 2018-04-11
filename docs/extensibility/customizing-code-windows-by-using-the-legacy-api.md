---
title: Personnalisation des fenêtres de Code à l’aide de l’API héritée | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f0b00c31280b9471da99aea55118e25dd551ad96
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personnalisation des fenêtres de Code à l’aide de l’API héritée
Une fenêtre de code est un objet de fenêtre de document qui prend en charge une ou plusieurs vues de texte. Les mêmes fonctionnalités d’une fenêtre de code dépendent du service de langage associé. En mode de l’interface multidocument (MDI), la fenêtre de code est l’enfant MDI.  
  
 Fenêtres de code sont contrôlées par les services de langage, et chaque service de langage peut fournir son propre gestionnaire de fenêtre de code. Ainsi, le service de langage ajouter ses propres motifs dans la fenêtre de code, tels que les tildes, la colorisation et bien plus encore. Pour plus d’informations sur la création d’une fenêtre principale, consultez [instanciation le cœur éditeur à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Une fenêtre de code est un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui a un affichage de texte et les ornements dans le site de l’objet. Lorsque vous créez la fenêtre de code pendant votre l’instanciation du noyau éditeur, votre service de langage peut attacher un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> à la fenêtre de code, comme est indiqué dans l’illustration suivante.  
  
 ![Graphique CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Fenêtre Code  
  
 Le service de langage implémente le Gestionnaire de fenêtre de code et est responsable de la gestion des ornements, comme une barre de menu déroulant. La fenêtre de code appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode lors de l’initialisation de fenêtre de code. Lorsque cet appel est effectué, le service de langage peut ajouter une barre de menu déroulant ou une barre de boutons (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) dans la fenêtre de code.  
  
## <a name="in-this-section"></a>Dans cette section  
 `Customizing Code Windows by Using the Legacy API`  
 Explique comment personnaliser des fenêtres de code à l’aide de l’API héritée.  
  
 [Comment : héberger un éditeur dans un autre éditeur](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explique comment héberger un second éditeur à l’intérieur d’une fenêtre d’éditeur.  
  
 [Comment : déclencher des événements lorsque l’éditeur perd le Focus](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explique comment attacher une vue de document à un objet de données du document.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)