---
title: IDebugDocumentTextEvents2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 242c15cc456c3a27ba7b7da45a11031b026c02d3
ms.lasthandoff: 04/05/2017

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
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Obtient cette interface via un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>méthode.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>interface est obtenue à partir d’un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>méthode.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>interface est obtenu en appelant le [QueryInterface](/cpp/atl/queryinterface) méthode sur une [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>  
  
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
  
## <a name="remarks"></a>Remarques  
 Seuls les moteurs de débogage qui fournissent leurs propres documents bénéficie de le `IDebugDocumentTextEvent2` interface. Un exemple serait un moteur de débogage de script. En cours de l’interprétation des scripts, nouveau code source peut être générée qui n’est pas présent dans n’importe quel fichier de disque et est connue uniquement du DE.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
