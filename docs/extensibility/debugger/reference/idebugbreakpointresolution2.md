---
title: IDebugBreakpointResolution2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
caps.latest.revision: 11
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b4d5c4ed0ad36f3eabcec9d943be53554b958a67
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Cette interface représente les informations qui décrivent un point d’arrêt lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBreakpointResolution2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt. Cette interface fournit une description d’un point d’arrêt lié par le Gestionnaire de session de débogage pour un utilisateur affiche les propriétés d’un point d’arrêt.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugBreakpointResolution2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtient le type de point d’arrêt représenté par cette solution.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution de point d’arrêt qui décrit ce point d’arrêt.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
