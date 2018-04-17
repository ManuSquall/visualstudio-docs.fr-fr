---
title: Affichage des variables locales | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03a3f08498e8b046b02defd32083677b7f39e7e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-locals"></a>Affichage des variables locales
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’exécution de toujours s’effectue dans le contexte d’une méthode, également connu sous le contenu dans la méthode ou de la méthode actuelle. Lorsque l’exécution s’arrête, Visual Studio appelle le moteur de débogage (DE) pour obtenir une liste de variables locales et les arguments, appelées collectivement les variables locales de la méthode. Visual Studio affiche ces variables locales et leurs valeurs dans le **variables locales** fenêtre.  
  
 Pour afficher les variables locales, appelle la DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthode appartenant à la EE et lui donne un contexte d’évaluation, qui est, un symbole fournisseur (SP), l’adresse en cours d’exécution et un objet de classeur. Pour plus d’informations, consultez [contexte d’évaluation](../../extensibility/debugger/evaluation-context.md). Si l’appel réussit, la `IDebugExpressionEvaluator::GetMethodProperty` méthode retourne un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente la méthode qui contient l’adresse en cours d’exécution.  
  
 Les appels DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet, qui est filtré pour retourner les seules variables locales et énumérée pour produire une liste de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)structures. Chaque structure contient le nom, le type et la valeur des variables locales. Le type et la valeur sont stockés sous forme de chaînes au format appropriés pour l’affichage. Le nom, le type et la valeur sont généralement affichés ensemble dans une ligne de la **variables locales** fenêtre.  
  
> [!NOTE]
>  Le **Espion express** et **espion** fenêtres affichent également des variables avec le même format de nom, valeur et type. Toutefois, ces valeurs sont obtenues en appelant [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) au lieu de `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemple d’implémentation de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Utilise des exemples pour parcourir le processus d’implémentation des variables locales.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Explique que lorsque le moteur de débogage (DE) appelle l’évaluateur d’expression (EE), il passe trois arguments.  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)