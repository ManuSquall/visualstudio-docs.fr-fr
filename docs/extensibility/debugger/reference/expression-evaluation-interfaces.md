---
title: Interfaces de l’évaluation d’expression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf5367d12593ae9789ff0529c76cc0494a6f99ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932270"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces d’évaluation des expressions
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Les éléments suivants sont les Interfaces d’évaluation d’Expression pour la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de débogage.  
  
## <a name="discussion"></a>Discussion  
 Ces interfaces sont utilisées pour évaluer des expressions dans une pile des appels en mode arrêt. Elles sont implémentées uniquement pour les évaluateurs d’expression au moment de l’exécution common language (EE).  
  
 Chaque interface dans le tableau affiche le composant que vous pouvez l’implémenter dans la liste suivante :  
  
-   Déboguer le moteur (DE)  
  
-   Évaluateur d’expression (EE)  
  
-   Visual Studio (VS)  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Représente un alias numérique pour une variable.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Représente un alias numérique pour une variable et permet un évaluateur d’expression (EE) pour obtenir le domaine d’application pour l’alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Représente un objet tableau.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Représente un objet de tableau managé et permet à un évaluateur d’expression (EE) pour déterminer l’index de base (limites inférieures) pour le tableau.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Représente un classeur que lie les symboles pour les adresses réelles dans la mémoire de débogage.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identique à la [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, mais fournit l’accès aux types, les alias et les visualiseurs personnalisés.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Représente l'évaluateur d'expression.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Représente une version améliorée d’un évaluateur d’expression (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Représente un évaluateur d’expression (EE) avec une arborescence d’analyseur améliorée.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Représente une fonction.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Représente une fonction et améliore la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permet à un évaluateur d’expression (EE) afficher un message dans la fenêtre de sortie du débogueur.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Représente un objet de code managé.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface de base qui représente n’importe quel symbole lié à une adresse mémoire.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identique à la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface, mais fournit l’accès à des informations supplémentaires.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Représente une expression analysée prête à être évaluée.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Représente un pointeur.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Représente un pointeur dans une arborescence d’analyse et étend le **IDebugPointerObject** interface.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilité de modifier la valeur d’un type via un visualiseur de type.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fournit l’accès aux visionneuses personnalisées et des visualiseurs de type.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Offre la possibilité de créer un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objet.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Représente une collection de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Écriture d’un évaluateur d’Expression de CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)