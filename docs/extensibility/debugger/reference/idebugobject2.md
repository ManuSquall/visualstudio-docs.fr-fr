---
title: IDebugObject2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
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
ms.openlocfilehash: dd3a3bed1e6994ff3c5fd32ded40a61929f4ca19
ms.lasthandoff: 04/05/2017

---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit des informations supplémentaires sur un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour offrir la prise en charge des alias et l’accès aux informations sur l’objet.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pouvez obtenir cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface). En outre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Outre les méthodes sur le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface, le `IDebugObject2` interface implémente les éléments suivants :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtient le champ ou la variable (le cas échéant) qui peut être stockage de la propriété représentée par cet objet.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtient l’objet de code managé qui représente la valeur de cet objet.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crée un ID unique pour cet objet ou retourne un alias existant.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtient l’alias associé à cet objet, le cas échéant.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtient le type de cet objet.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Détermine si cet objet représente les données utilisateur.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Détermine si l’état de modifier & Continuer n’est plus valide.<br /><br /> Un évaluateur d’expression personnalisée n’implémente pas cette méthode (elle doit toujours retourner `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Remarques  
 Consultez [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) pour en savoir plus sur les alias.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [Fonction GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
