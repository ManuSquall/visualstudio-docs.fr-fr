---
title: "IDebugExpressionContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "Interface de IDebugExpressionContext2"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un contexte pour l'évaluation de l'expression  
  
## Syntaxe  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour représenter un contexte dans lequel une expression sera évaluée.  
  
## Remarques pour les appelants  
 Un appel à [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne cette interface.  Cette interface est accessible uniquement lorsque le programme débogué a été suspendu et un frame de pile est disponible.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugExpressionContext2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetName](../Topic/IDebugExpressionContext2::GetName.md)|extrait le nom du contexte d'évaluation.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analyse une expression basée sur une texte pour l'évaluation.|  
  
## Notes  
 Un contexte d'évaluation peut être considéré comme place de l'évaluation d'une expression.  
  
 Lorsqu'un programme a désactivé, le gestionnaire de débogage de session \(SDM\) obtient un frame de pile du De avec un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir l'interface d' `IDebugExpressionContext2` .  Cela est suivi par un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer une interface d' [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , qui représente l'expression analysée prête à être évalué.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)