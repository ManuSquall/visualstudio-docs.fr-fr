---
title: Affichage des sections locales ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738932"
---
# <a name="display-locals"></a>Afficher les habitants
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’exécution a toujours lieu dans le contexte d’une méthode, également connue sous le nom de méthode contenante ou méthode actuelle. Lorsque l’exécution s’arrête, Visual Studio appelle le moteur de débogé (DE) pour obtenir une liste de variables et d’arguments locaux, collectivement appelés les habitants de la méthode. Visual Studio affiche ces habitants et leurs valeurs dans la fenêtre **des sections locales.**

 Pour afficher les habitants, le DE appelle la méthode [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) appartenant à l’EE et lui donne un contexte d’évaluation, c’est-à-dire un fournisseur de symboles (SP), l’adresse d’exécution actuelle, et un objet de liant. Pour plus d’informations, voir [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md). Si l’appel réussit, la `IDebugExpressionEvaluator::GetMethodProperty` méthode renvoie un objet [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) qui représente la méthode qui contient l’adresse d’exécution actuelle.

 Le DE appelle [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir un objet [IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) qui est filtré pour retourner uniquement les habitants et énumérés pour produire une liste de [structures DEBUG_PROPERTY_INFO.](../../extensibility/debugger/reference/debug-property-info.md) Chaque structure contient le nom, le type et la valeur d’un local. Le type et la valeur sont stockés sous forme de cordes formatées, adaptées à l’affichage. Le nom, le type et la valeur sont généralement affichés ensemble dans une ligne de la fenêtre **local.**

> [!NOTE]
> Les fenêtres **QuickWatch** et **Watch** affichent également des variables avec le même format de nom, de valeur et de type. Cependant, ces valeurs sont obtenues en appelant `IDebugProperty2::EnumChildren` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) au lieu de .

## <a name="in-this-section"></a>Contenu de cette section
 [Exemple de mise en œuvre des habitants](../../extensibility/debugger/sample-implementation-of-locals.md) Utilise des exemples pour passer à travers le processus de mise en œuvre des habitants.

## <a name="related-sections"></a>Sections connexes
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) Explique que lorsque le moteur de débogé (DE) appelle l’évaluateur d’expression (EE), il passe trois arguments.

## <a name="see-also"></a>Voir aussi
 [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
