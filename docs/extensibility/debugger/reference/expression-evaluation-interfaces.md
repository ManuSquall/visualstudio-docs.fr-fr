---
title: "Interfaces de l’évaluation d’expression | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a5ce9f82e88c6275000c17d40e2b1e1494683715
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de l’évaluation d’expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Les éléments suivants sont les Interfaces d’évaluation d’Expression pour la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Kit de développement logiciel de débogage.  
  
## <a name="discussion"></a>Discussion  
 Ces interfaces sont utilisées pour évaluer des expressions dans une pile d’appels en mode arrêt. Elles sont implémentées uniquement pour le common language runtime évaluateurs d’expressions (EE).  
  
 Chaque interface dans le tableau affiche le composant que vous pouvez l’implémenter à partir de la liste suivante :  
  
-   Déboguer le moteur (DE)  
  
-   Évaluateur d’expression (EE)  
  
-   Visual Studio (Visual Studio)  
  
|Interface|Implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Représente un alias numérique pour une variable.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Représente un alias numérique pour une variable et permet l’évaluateur d’expression (EE) pour obtenir le domaine d’application pour l’alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Représente un objet tableau.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Représente un objet de tableau managé et permet à un évaluateur d’expression (EE) pour déterminer l’index de base (limites inférieures) pour le tableau.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Représente un classeur que lie les symboles pour les adresses réelles dans la mémoire de débogage.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identique à la [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, mais permet d’accéder aux types, les alias et les visualiseurs personnalisés.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Représente l'évaluateur d'expression.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Représente une version améliorée de l’évaluateur d’expression (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Représente l’évaluateur d’expression (EE) avec une arborescence de l’analyseur améliorée.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Représente une fonction.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Représente une fonction et améliore la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permet à un évaluateur d’expression (EE) afficher un message dans la fenêtre de sortie du débogueur.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Représente un objet de code managé.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface de base qui représente n’importe quel symbole lié à une adresse mémoire.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identique à la [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) mais donne accès aux informations supplémentaires.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Représente une expression analysée prête à être évaluée.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Représente un pointeur.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Représente un pointeur dans une arborescence d’analyse et étend la **IDebugPointerObject** interface.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Fournit la possibilité de modifier la valeur d’un type via un visualiseur de type.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fournit l’accès aux visualiseurs de types et les visionneuses personnalisées.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Offre la possibilité de créer un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objet.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Représente une collection de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objets.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [L’écriture d’un évaluateur d’Expression CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)