---
title: IDebugDocumentTextEvents2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f34bb09847659fdfc1dfcbd036aef2a47c8bd5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Cette interface est utilisée pour notifier Visual Studio sur les modifications apportées à la source qui sont fournies par le moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour prendre en charge d’apporter des modifications au code source. Cette interface est généralement implémentée sur le même objet qui implémente le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Obtient cette interface via un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> (méthode). Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est obtenue à partir d’un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> (méthode). Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface est obtenu en appelant le [QueryInterface](/cpp/atl/queryinterface) méthode sur une [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocumentTextEvents2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indique que la totalité du document a été détruit.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifie le package de débogage que le texte a été insérée dans le document.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifie le package de débogage que le texte a été supprimé du document.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifie le package de débogage que le texte a été remplacé dans le document.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifie le package de débogage que les attributs de texte ont été mis à jour dans le document.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifie le récepteur de l’événement que les attributs du document ont été mis à jour.|  
  
## <a name="remarks"></a>Notes  
 Seuls les moteurs de débogage qui fournissent leurs propres documents bénéficie de le `IDebugDocumentTextEvent2` interface. Un exemple serait un moteur de débogage de script. En cours de l’interprétation des scripts, nouveau code source peut être générée qui n’est pas présent dans n’importe quel fichier de disque et est connue uniquement du DE.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)