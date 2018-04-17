---
title: IDebugReference2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5d5d8b3ab6e608a2454847fc9ec27e384777bc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2"></a>IDebugReference2
Cette interface représente une référence à une propriété de frame de pile ou une autre propriété.  
  
> [!NOTE]
>  `IDebugReference2` est réservé pour une utilisation ultérieure et tous ses méthodes doivent retourner `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour représenter une référence à un type particulier de valeur. Par exemple, la valeur peut être une valeur numérique à la suite d’une évaluation d’expression, un contexte de la mémoire utilisée pour l’affichage de mémoire ou une liste des registres et leurs valeurs.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) pour obtenir cette interface. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) et [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) également retourner cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugReference2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtient le [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure qui décrit cette référence.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Définit la valeur de cette référence à partir d’une chaîne.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Définit la valeur de cette référence à partir d’une autre référence.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Énumère les enfants de cette référence.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtient le parent de cette référence.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtient la référence de la plus dérivée de cette référence.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtient les octets de mémoire à laquelle cette référence fait référence.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtient un contexte de la mémoire pour cette référence.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtient la taille, en octets, de cette référence.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Définit ce type de référence.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compare cette référence avec un autre.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette utilisation de « propriété » ne doit pas être confondue avec cette variable de membre d’une classe, ce qui signifie que même si un `IDebugReference2` peut représenter une telle entité.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) représente une propriété, tandis que `IDebugReference2` représente une référence à une propriété, en général, une référence à un objet dans le programme en cours de débogage.  
  
 La principale différence entre une propriété et une référence est qu’une propriété fait référence à une instance nommée d’un objet, tandis qu’une référence à une instance sans nom. Par exemple, une propriété peut faire référence à un objet dans le tas du programme par `"a.b"`. Une autre propriété peut faire référence au même objet en tant que `"c.d"`. La façon de faire référence à cette propriété requiert que `"a.b"` ou `"c.d"` être dans la portée. Une référence à ce même objet est sans nom ; l’objet peut être référencé tant que la mémoire pour cet objet est valide.  
  
 Un `IDebugProperty2` interface peut être considéré comme une valeur avec un nom, un type et une adresse. Un `IDebugReference2`sur l’autre revanche, peut être considéré comme un type et une adresse.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)