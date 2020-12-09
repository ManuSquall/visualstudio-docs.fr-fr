---
title: Affichage des variables locales | Microsoft Docs
description: En savoir plus sur la liste des variables locales et des arguments, collectivement appelés les variables locales de la méthode, qui sont affichées lorsque l’exécution est suspendue.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ddc7bc564e4e294144eeb3fa34db8bdf73971053
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915542"
---
# <a name="display-locals"></a>Afficher les variables locales
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’exécution a toujours lieu dans le contexte d’une méthode, également appelée méthode conteneur ou méthode actuelle. Lorsque l’exécution est suspendue, Visual Studio appelle le moteur de débogage (DE) pour obtenir une liste de variables locales et d’arguments, collectivement appelés les variables locales de la méthode. Visual Studio affiche ces variables locales et leurs valeurs dans la fenêtre **variables locales** .

 Pour afficher les variables locales, le paramètre DE appelle la méthode [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) qui appartient à EE et lui donne un contexte d’évaluation, autrement dit, un fournisseur de symboles (SP), l’adresse d’exécution actuelle et un objet Binder. Pour plus d’informations, consultez la section [contexte d’évaluation](../../extensibility/debugger/evaluation-context.md). Si l’appel a échoué, la `IDebugExpressionEvaluator::GetMethodProperty` méthode retourne un objet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , qui représente la méthode qui contient l’adresse d’exécution actuelle.

 L’appel DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir un objet [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , qui est filtré pour retourner uniquement les variables locales et énumérées pour produire une liste de structures de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) . Chaque structure contient le nom, le type et la valeur d’un local. Le type et la valeur sont stockés sous forme de chaînes mises en forme, pouvant être affichées. Le nom, le type et la valeur sont généralement affichés ensemble sur une seule ligne de la fenêtre **variables locales** .

> [!NOTE]
> Les fenêtres **Espion express** et **Espion** affichent également des variables avec le même format de nom, de valeur et de type. Toutefois, ces valeurs sont obtenues en appelant [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) au lieu de `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>Dans cette section
 [Exemple d’implémentation de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md) Utilise des exemples pour parcourir le processus d’implémentation des variables locales.

## <a name="related-sections"></a>Sections connexes
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) Explique que lorsque le moteur DE débogage (DE) appelle l’évaluateur d’expression (EE), il passe trois arguments.

## <a name="see-also"></a>Voir aussi
 [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
