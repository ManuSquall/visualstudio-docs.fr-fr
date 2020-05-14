---
title: Interfaces d’évaluation de l’expression (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736942"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces d’évaluation des expressions
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Voici les interfaces d’évaluation [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] d’expression pour le Debugging SDK.

## <a name="discussion"></a>Discussions
 Ces interfaces sont utilisées pour évaluer les expressions dans une pile d’appels pendant le mode de rupture. Ils ne sont mis en œuvre que pour les évaluateurs d’expression de temps de course de langue (EE).

 Chaque interface dans le tableau affiche le composant qui peut l’implémenter à partir de la liste suivante :

- Moteur Debug (DE)

- Évaluateur d’expression (EE)

- Studio visuel (VS)

|Interface|Mis en œuvre par|Description|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Représente un alias numérique pour une variable.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Représente un alias numérique pour une variable, et permet à un évaluateur d’expression (EE) d’obtenir le domaine d’application pour l’alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Représente un objet tableau.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Représente un objet de tableau géré, et permet à un évaluateur d’expression (EE) de déterminer l’indice de base (limites inférieures) pour le tableau.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Représente un liant qui lie les symboles de débogé à des adresses réelles dans la mémoire.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Tout comme l’interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) mais donne accès à des types, des alias et des visualisateurs personnalisés.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Représente l'évaluateur d'expression.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Représente une version améliorée d’un évaluateur d’expression (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Représente un évaluateur d’expression (EE) avec un arbre de paroisseur amélioré.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Représente une fonction.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Représente une fonction et améliore l’interface [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permet à un évaluateur d’expression (EE) d’afficher un message dans la fenêtre de sortie du débaugeant.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Représente un objet de code géré.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface de base qui représente n’importe quel symbole lié à une adresse mémoire.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Tout comme l’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) mais donne accès à des informations supplémentaires.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Représente une expression analysée prête à être évaluée.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Représente un pointeur.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Représente un pointeur dans un arbre d’analyse, et étend l’interface **IDebugPointerObject.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Fournit la possibilité de modifier la valeur d’un type par le biais d’un visualiseur de type.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Donne accès à des spectateurs personnalisés et à des visualisateurs de type.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Fournit la possibilité de créer un objet [IEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Représente une collection d’objets [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)|

## <a name="see-also"></a>Voir aussi
- [Référence des API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Écriture d’un évaluateur d’expression de CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
