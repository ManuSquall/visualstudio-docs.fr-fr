---
title: Objet VSCodeWindow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690771"
---
# <a name="vscodewindow-object"></a>Objet VSCodeWindow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fenêtre de code est une fenêtre de document spécialisé qui peut inclure une ou plusieurs vues de texte, généralement le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
 Point de vue architectural, la fenêtre de code est une fenêtre de document qui se trouve dans un frame de fenêtre. Point de vue fonctionnel, la fenêtre de code est simplement une fenêtre de document avec des fonctionnalités supplémentaires. Dans le mode d’interface multidocument (MDI), la fenêtre de code est le frame enfant MDI. Pour plus d’informations, consultez [personnalisation de Code Windows à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Le tableau suivant contient les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objet.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fournit un mécanisme d’accès génériques pour rechercher un service qui identifie un identificateur global unique (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Représente un enfant d’interface (multidocument MDI) document plusieurs contenant une ou plusieurs vues de code.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Remplit un frame de fenêtre.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Édition de figures](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
