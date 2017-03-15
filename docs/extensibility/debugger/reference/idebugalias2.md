---
title: "IDebugAlias2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugAlias2"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un alias pour une variable numérique et permet un évaluateur d’expression \(EE\) pour obtenir le domaine d’application pour l’alias.  
  
## Syntaxe  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Cette interface est implémentée par le moteur de débogage managés \(DE\).  
  
## Méthodes  
 Outre les méthodes sur le [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Récupère l’identificateur pour le domaine d’application.|  
  
## Notes  
 Un alias est un nombre décimal sous forme de chaîne suivie du caractère \#, par exemple, 1001\#.  
  
## Configuration requise  
 En\-tête : Ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll