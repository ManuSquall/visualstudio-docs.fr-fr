---
title: "IDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject"
helpviewer_keywords: 
  - "Interface de IDebugObject"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente un objet binder crée pour encapsuler les valeurs de symboles et d’expressions.  
  
## Syntaxe  
  
```  
IDebugObject : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Un évaluateur d’expression implémente cette interface pour représenter un objet.  
  
## Remarques pour les appelants  
 Cette interface est la classe de base pour tous les objets que l’évaluateur d’expression utilise dans des expressions analysées. Il est retourné par un appel à la [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md) \(méthode\).[QueryInterface](/visual-cpp/atl/queryinterface) Obtient les interfaces plus spécialisées à partir de cette interface.  
  
## Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugObject`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtient la taille de l’objet.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtient la valeur de l’objet sous la forme d’une série d’octets consécutif.|  
|[SetValue](../Topic/IDebugObject::SetValue.md)|Définit la valeur de l’objet à partir d’une série d’octets consécutif.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Définit la valeur de référence de cet objet.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtient le contexte de la mémoire qui représente l’adresse de la valeur de l’objet.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.|  
|[IsNullReference](../Topic/IDebugObject::IsNullReference.md)|Teste si cet objet est une référence null.|  
|[IsEqual](../Topic/IDebugObject::IsEqual.md)|Compare un objet à celui\-ci.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Détermine si cet objet est en lecture seule.|  
|[Proxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Détermine si l’objet est un proxy transparent.|  
  
## Notes  
 L’évaluateur d’expression utilise cette interface comme classe de base pour représenter des objets dans une arborescence d’analyse.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../Topic/IDebugArrayObject::GetElement.md)   
 [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)