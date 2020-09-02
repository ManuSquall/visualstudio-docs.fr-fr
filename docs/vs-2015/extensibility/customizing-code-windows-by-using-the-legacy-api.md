---
title: Personnalisation des fenêtres de code à l’aide de l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556122"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personnalisation des fenêtres de code à l’aide de l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fenêtre de code est un objet de fenêtre de document qui prend en charge un ou plusieurs affichages de texte. Les fonctionnalités exactes d’une fenêtre de code dépendent du service de langage associé. En mode MDI (multiple-document interface), la fenêtre de code est le frame enfant MDI.  
  
 Les fenêtres de code sont contrôlées par les services de langage, et chaque service de langage peut fournir son propre gestionnaire de fenêtre de code. Cela permet au service de langage d’ajouter ses propres ornements à la fenêtre de code, tels que les tildes, la colorisation, etc. Pour plus d’informations sur la création d’une fenêtre principale, consultez [instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Une fenêtre de code est un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objet qui a un affichage de texte et tous les ornements faisant l’objet d’un site dans l’objet. Lorsque vous créez la fenêtre de code pendant votre instanciation de l’éditeur principal, votre service de langage peut attacher un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> à la fenêtre de code, comme indiqué dans l’illustration suivante.  
  
 ![Graphique de CodeWindow](../extensibility/media/vscodewindow.gif "VsCodeWindow")  
Fenêtre de code  
  
 Le service de langage implémente le gestionnaire de fenêtre de code et est chargé de gérer les ornements, tels qu’une barre de liste déroulante. La fenêtre de code appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> méthode pendant l’initialisation de la fenêtre de code. Lorsque cet appel est effectué, le service de langage peut ajouter une barre déroulante ou une barre de boutons ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ) à la fenêtre de code.  
  
## <a name="in-this-section"></a>Dans cette section  
 `Customizing Code Windows by Using the Legacy API`  
 Explique comment personnaliser les fenêtres de code à l’aide de l’API héritée.  
  
 [Guide pratique pour héberger un éditeur dans un autre éditeur](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explique comment héberger un deuxième éditeur dans une fenêtre d’éditeur.  
  
 [Guide pratique pour déclencher des événements quand l’éditeur perd le focus](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explique comment attacher une vue de document à un objet de données de document.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Accès à la vue texte à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
