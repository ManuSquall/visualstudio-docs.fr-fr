---
title: Objet de VSCodeWindow | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0b114db98f5a8a50065c8a3219dc4179787c738
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="vscodewindow-object"></a>Objet de VSCodeWindow
Une fenêtre de code est une fenêtre de document spécialisé qui peut inclure une ou plusieurs vues de texte, généralement le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
 Point de vue architectural, la fenêtre de code est une fenêtre de document qui se trouve dans un frame de fenêtre. Point de vue fonctionnel, la fenêtre de code est simplement une fenêtre de document avec des fonctionnalités supplémentaires. Dans le mode de l’interface multidocument (MDI), la fenêtre de code est l’enfant MDI. Pour plus d’informations, consultez [personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Le tableau suivant présente les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objet.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fournit un mécanisme d’accès générique pour rechercher un service qui identifie par un identificateur global unique (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Représente un enfant d’interface (multidocument MDI) document plusieurs contenant une ou plusieurs vues de code.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Remplit un frame de fenêtre.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Modifier des chiffres](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)