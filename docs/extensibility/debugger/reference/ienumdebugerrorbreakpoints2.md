---
title: IEnumDebugErrorBreakpoints2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 9
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
ms.openlocfilehash: 39b2ce4bb8fdecbe67d6c39e53454e49853f55c8
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Cette interface énumère les points d’arrêt de l’erreur associées à un point d’arrêt en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appels de Visual Studio [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) pour obtenir cette interface qui représente une liste des points d’arrêt ne peut pas être liée, ou [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) pour obtenir cette interface qui représente une liste de points d’arrêt qui n’étaient pas liés.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugErrorBreakpoints2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Récupère un nombre spécifié de points d’arrêt de l’erreur dans une séquence d’énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignore un nombre spécifié de points d’arrêt de l’erreur dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtient le nombre de points d’arrêt de l’erreur dans l’énumérateur.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface conserve une liste de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaces, qui décrivent chacune un point d’arrêt qui ne peut pas être lié et pourquoi il ne peut pas être lié. Visual Studio utilise le `IEnumDebugErrorBreakpoint2` interface pour mettre à jour les points d’arrêt affichées dans l’IDE.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
