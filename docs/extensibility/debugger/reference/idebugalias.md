---
title: IDebugAlias | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 128dc9001faba06b1c95c5ebc364f319891ce409
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un alias numérique pour une variable. Un alias est simplement un nom différent pour une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression (EE) implémente cette interface pour prendre en charge les alias numériques pour les variables.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crée un alias pour un objet particulier. Pour rechercher des alias, utilisez [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) ou [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Les méthodes suivantes sont définies dans le `IDebugAlias` interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Fonction GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtient l’objet auquel fait référence cet alias.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtient le nom d’alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Récupère un `ICorDebugValue` interface qui fournit l’accès à des informations sur le code sur cet objet (code managé uniquement) managé.|  
|[Méthode dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marque cet alias comme n’étant plus utilisé.|  
  
## <a name="remarks"></a>Remarques  
 Un alias est un nombre décimal sous forme de chaîne suivi par le caractère #, par exemple, 1001#.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)