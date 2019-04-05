---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 848a03b5b254982298d170b72aaea1a538939276
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952558"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit des informations supplémentaires sur un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour offrir la prise en charge des alias et l’accès aux informations sur l’objet.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface peut obtenir cette interface à l’aide de [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). En outre, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Outre les méthodes sur le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface, le `IDebugObject2` interface implémente les éléments suivants :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Obtient le champ ou la variable (le cas échéant) qui peut être sauvegarde de la propriété représentée par cet objet.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Obtient l’objet de code managé qui représente la valeur de cet objet.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Crée un ID unique pour cet objet, ou retourne un alias existant.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Obtient l’alias associé à cet objet, le cas échéant.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Obtient le type de cet objet.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Détermine si cet objet représente les données utilisateur.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Détermine si l’état de modifier & Continuer n’est plus valide.<br /><br /> Un évaluateur d’expression personnalisée n’implémente pas cette méthode (elle doit toujours retourner `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Notes  
 Consultez [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) pour une discussion sur les alias.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
