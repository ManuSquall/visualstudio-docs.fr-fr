---
title: "IDebugAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias"
helpviewer_keywords: 
  - "Interface de IDebugAlias"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d'implémenter des évaluateurs d'expression est déconseillée. Pour plus d'informations sur l'implémentation des évaluateurs d'expression CLR, consultez [évaluateurs d'Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d'évaluateur d'Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un alias pour une variable numérique. Un alias est simplement un nom différent pour une variable.  
  
## Syntaxe  
  
```  
IDebugAlias : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 L'évaluateur d'expression \(EE\) implémente cette interface pour prendre en charge les alias numériques pour les variables.  
  
## Remarques pour les appelants  
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md) Crée un alias pour un objet particulier. Pour rechercher des alias, utilisez [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) ou [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## Méthodes dans l'ordre Vtable  
 Les méthodes suivantes sont définies dans le `IDebugAlias` interface.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtient l'objet auquel cet alias fait référence.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtient le nom d'alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Récupère un `ICorDebugValue` interface qui fournit l'accès à des informations sur le code sur cet objet \(code managé uniquement\) managé.|  
|[Méthode dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marque cet alias n'est plus utilisé.|  
  
## Notes  
 Un alias est un nombre décimal sous forme de chaîne suivie du caractère \#, par exemple, 1001\#.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)