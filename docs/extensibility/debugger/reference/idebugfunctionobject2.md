---
title: "IDebugFunctionObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugFunctionObject2"
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente une fonction et améliore la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
## Syntaxe  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Un évaluateur d’expression \(EE\) implémente cette interface pour représenter une fonction.  
  
## Remarques pour les appelants  
 Méthodes de cette interface différeront de ceux de **IDebugFunctionObject** comme suit :  
  
-   Le **IDebugEvaluate** méthode accepte des indicateurs.  
  
-   Le **CreateObject** méthode prend un délai d’attente et les indicateurs.  
  
-   Le **CreateStringObjectWithLength** méthode prend une longueur.  
  
## Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crée un objet qui utilise un constructeur avec des paramètres d’évaluation de l’indicateur et une valeur de délai d’attente.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crée un objet de chaîne qui a une longueur spécifiée.|  
|[Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Appelle la fonction et retourne la valeur obtenue en tant qu’objet.|  
  
## Configuration requise  
 En\-tête : Ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll