---
title: "Interfaces de l&#39;&#233;valuation d&#39;expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation d'expression, interfaces"
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Interfaces de l&#39;&#233;valuation d&#39;expression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d'implémenter des évaluateurs d'expression est déconseillée. Pour plus d'informations sur l'implémentation des évaluateurs d'expression CLR, consultez [évaluateurs d'Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d'évaluateur d'Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Les éléments suivants sont les Interfaces d'évaluation d'Expression pour la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de débogage.  
  
## Discussion  
 Ces interfaces sont utilisées pour évaluer des expressions dans une pile d'appels en mode arrêt. Elles sont implémentées uniquement pour les évaluateurs d'expression au moment de l'exécution commun language \(EE\).  
  
 Chaque interface dans le tableau indique le composant que vous pouvez l'implémenter à partir de la liste suivante :  
  
-   Déboguer le moteur \(DE\)  
  
-   Évaluateur d'expression \(EE\)  
  
-   Visual Studio \(VS\)  
  
|Interface|Implémentée par|Description|  
|---------------|---------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Représente un alias pour une variable numérique.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Représente un alias pour une variable numérique et permet un évaluateur d'expression \(EE\) pour obtenir le domaine d'application pour l'alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Représente un objet tableau.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Représente un objet de tableau managé et permet un évaluateur d'expression \(EE\) pour déterminer l'index de base \(limite inférieure\) pour le tableau.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Représente un classeur que lie les symboles pour les adresses réelles dans la mémoire de débogage.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identique à la [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, mais permet d'accéder aux visualiseurs personnalisés, les alias et les types.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Représente l'évaluateur d'expression.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Représente une version améliorée d'un évaluateur d'expression \(EE\).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Représente un évaluateur d'expression \(EE\) avec une arborescence d'analyse améliorée.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Représente une fonction.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Représente une fonction et améliore la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permet à un évaluateur d'expression \(EE\) afficher un message dans la fenêtre de sortie du débogueur.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Représente un objet de code managé.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface de base qui représente n'importe quel symbole lié à une adresse mémoire.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identique à la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) mais donne accès aux informations supplémentaires.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Représente une expression analysée prête à être évaluée.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Représente un pointeur.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Représente un pointeur dans une arborescence d'analyse et étend la **IDebugPointerObject** interface.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilité de modifier la valeur d'un type dans un visualiseur de type.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VISUAL STUDIO|Fournit l'accès aux visionneuses personnalisées et des visualisations de type.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VISUAL STUDIO|Permet de créer un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objet.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Représente une collection d'objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md).|  
  
## Voir aussi  
 [Référence API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Écriture d'un évaluateur d'Expression CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)