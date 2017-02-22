---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugExpressionEvaluator2"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente une version améliorée d’un évaluateur d’expression \(EE\).  
  
## Syntaxe  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Cette interface est implémentée par un évaluateur d’expression.  
  
## Méthodes  
 Outre les méthodes sur le [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Récupère un objet de service donné son identificateur unique.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Précharge les modules désignés par le fournisseur de symbole spécifiés.|  
|[SetCallback](../Topic/IDebugExpressionEvaluator2::SetCallback.md)|Permet à l’évaluateur d’expression \(EE\) spécifier l’interface de rappel que le moteur du débogueur \(DE\) utilise pour lire les paramètres de mesure.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Définit le chemin d’accès pour le common language runtime \(CLR\) chargé dans le débogueur.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Permet de transférer un rappel à l’évaluateur d’expression lors de l’initialisation, un moteur de débogage.|  
|[Terminer](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Arrête et nettoie l’évaluateur d’expression.|  
  
## Configuration requise  
 En\-tête : Ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll