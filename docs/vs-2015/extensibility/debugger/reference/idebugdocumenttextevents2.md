---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dca9d3c8de956faf2dab5c9090c9963a7c9fbea0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950673"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface est utilisée pour notifier Visual Studio sur les modifications apportées au document source qui sont fournies par le moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le D’implémente cette interface pour prendre en charge d’apporter des modifications au code source. Cette interface est généralement implémentée sur le même objet qui implémente le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Obtient cette interface via un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> (méthode). Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est obtenue à partir d’un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> (méthode). Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface est obtenue en appelant le [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) méthode sur un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocumentTextEvents2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indique que la totalité du document a été détruit.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Informe le package de débogage que le texte a été inséré dans le document.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Informe le package de débogage que le texte a été supprimé à partir du document.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Informe le package de débogage que le texte a été remplacé dans le document.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Informe le package de débogage que les attributs de texte ont été mis à jour dans le document.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifie le récepteur de l’événement que les attributs de document ont été mis à jour.|  
  
## <a name="remarks"></a>Notes  
 Uniquement les moteurs de débogage qui fournissent leurs propres documents bénéficie de la `IDebugDocumentTextEvent2` interface. Un exemple de ce serait un moteur de débogage de script. En cours d’interprétation des scripts, nouveau code source peut être générée qui n’est pas présent dans n’importe quel fichier de disque et est connue uniquement de l’Allemagne.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
