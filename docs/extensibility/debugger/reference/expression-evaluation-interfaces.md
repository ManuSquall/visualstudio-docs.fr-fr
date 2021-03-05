---
description: Voici les interfaces d’évaluation d’expression pour le kit de développement logiciel (SDK) de débogage Visual Studio.
title: Interfaces d’évaluation d’expression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d380fcce087fad3dc6b101e78cbc514ba19b1052
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158733"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces d’évaluation des expressions
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Voici les interfaces d’évaluation d’expression pour le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Kit de développement logiciel (SDK) de débogage.

## <a name="discussion"></a>Discussions
 Ces interfaces sont utilisées pour évaluer des expressions dans une pile des appels en mode arrêt. Elles sont implémentées uniquement pour les évaluateurs d’expression de Common Language Runtime (EE).

 Chaque interface du tableau indique le composant qui peut l’implémenter à partir de la liste suivante :

- Moteur DE débogage (DE)

- Évaluateur d’expression (EE)

- Visual Studio (VS)

|Interface|Implémenté par|Description|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Représente un alias numérique pour une variable.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Représente un alias numérique pour une variable et permet à un évaluateur d’expression (EE) d’obtenir le domaine d’application pour l’alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Représente un objet tableau.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Représente un objet tableau managé et permet à un évaluateur d’expression (EE) de déterminer l’index de base (limites inférieures) du tableau.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Représente un Binder qui lie des symboles de débogage à des adresses réelles en mémoire.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Identique à l’interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , mais permet d’accéder aux types, aux alias et aux visualiseurs personnalisés.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Représente l'évaluateur d'expression.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Représente une version améliorée d’un évaluateur d’expression (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Représente un évaluateur d’expression (EE) avec une arborescence d’analyseur améliorée.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Représente une fonction.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Représente une fonction et améliore l’interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Active un évaluateur d’expression (EE) pour afficher un message dans la fenêtre sortie du débogueur.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Représente un objet de code managé.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface de base qui représente tout symbole lié à une adresse mémoire.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Identique à l’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , mais permet d’accéder à des informations supplémentaires.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Représente une expression analysée prête à être évaluée.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Représente un pointeur.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Représente un pointeur dans une arborescence d’analyse et étend l’interface **IDebugPointerObject** .|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilité de modifier la valeur d’un type par le biais d’un visualiseur de type.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fournit l’accès aux visualiseurs personnalisés et aux visualiseurs de type.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Offre la possibilité de créer un objet [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Représente une collection d’objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .|

## <a name="see-also"></a>Voir aussi
- [Référence sur l’API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Écriture d’un évaluateur d’expression de CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
