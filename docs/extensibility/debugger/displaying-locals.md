---
title: "Afficher les variables locales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de l’expression [Debugging SDK], le débogage"
  - "évaluation d’expression, afficher les variables locales"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Afficher les variables locales
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’exécution de toujours s’effectue dans le contexte d’une méthode, également appelé la méthode conteneur ou la méthode actuelle. Lors de l’exécution est suspendue, Visual Studio appelle le moteur de débogage \(DE\) pour obtenir une liste de variables locales et les arguments, appelés collectivement les variables locales de la méthode. Visual Studio affiche les variables locales et leurs valeurs dans le **variables locales** fenêtre.  
  
 Pour afficher les variables locales, appelle la DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthode appartenant à la EE et lui donne un contexte d’évaluation, c'est\-à\-dire, un symbole fournisseur \(SP\), l’adresse en cours d’exécution et un objet binder. Pour plus d'informations, consultez [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md). Si l’appel réussit, la `IDebugExpressionEvaluator::GetMethodProperty` méthode renvoie une [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente la méthode qui contient l’adresse en cours d’exécution.  
  
 Les appels DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet, qui est filtrée pour renvoyer uniquement variables locales et énumérée pour produire une liste de [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) des structures. Chaque structure contient le nom, le type et la valeur d’une variable locale. Le type et la valeur sont stockées sous forme de chaînes au format appropriés pour l’affichage. Le nom, le type et la valeur sont généralement affichés ensemble dans une seule ligne de la **variables locales** fenêtre.  
  
> [!NOTE]
>  Le **Espion express** et **Espion** windows affichent également les variables avec le même format de nom, valeur et type. Toutefois, ces valeurs sont obtenues en appelant [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) au lieu de `IDebugProperty2::EnumChildren`.  
  
## Dans cette section  
 [Exemple d'implémentation des variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Utilise des exemples pas à pas le processus d’implémentation des variables locales.  
  
## Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Explique que lorsque le moteur de débogage \(DE\) appelle l’évaluateur d’expression \(EE\), il passe trois arguments.  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)