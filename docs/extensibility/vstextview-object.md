---
title: Objet de VSTextView | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5be89d01a668fd05e70e73e31ffaf3742317c272
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="vstextview-object"></a>Objet de VSTextView
L’affichage de texte est une fenêtre qui permet aux utilisateurs d’afficher et modifier le texte de la mémoire tampon de texte Unicode. Essentiellement, la vue est ce que la plupart des utilisateurs font référence en tant que l’éditeur. Étant donné que la vue est séparée de la mémoire tampon par différentes couches de texte (le retour automatique à texte en mode plan et ainsi de suite), la vue n’est pas garantie pour être une représentation exacte du texte dans la mémoire tampon. Pour plus d’informations sur l’affichage de texte, consultez [l’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Le tableau suivant montre les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
|Interface|Description|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interface standard OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface standard OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface standard OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface standard OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composées (autrement dit, les actions qui sont regroupées dans une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour la gestion et l’accès à la vue. `IVsTextView` n’est pas thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère un volet de fenêtre.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les couches de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un autre thread.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des chiffres](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objet de VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [L’accès à theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)