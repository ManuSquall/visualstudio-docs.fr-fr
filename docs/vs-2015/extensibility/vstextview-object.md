---
title: Objet VSTextView | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a09a4911eca71565b39ffdfab3cc31ec92233e06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501445"
---
# <a name="vstextview-object"></a>Objet VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [objet VSTextView](https://docs.microsoft.com/visualstudio/extensibility/vstextview-object).  
  
L’affichage de texte est une fenêtre qui permet aux utilisateurs d’afficher et modifier le texte Unicode de la mémoire tampon de texte. La vue est essentiellement ce que la plupart des utilisateurs font référence en tant que l’éditeur. Étant donné que la vue est séparée de la mémoire tampon par les différentes couches de texte (le retour automatique à texte en mode plan et ainsi de suite), la vue n’est pas garantie pour être une représentation exacte du texte dans la mémoire tampon. Pour plus d’informations sur l’affichage de texte, consultez [accès theText vue à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Le tableau suivant présente les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
|Interface|Description|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composites (autrement dit, les actions qui sont regroupées dans une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fournit les méthodes de base pour la gestion et l’accès à la vue. `IVsTextView` n’est pas thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crée et gère un volet de fenêtre.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagit avec les couches de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Effectue des opérations sur la vue à partir d’un thread différent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Édition de figures](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objet VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Accès au mode texte à l’aide de l’API héritée](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

