---
title: Affichage des variables locales | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e82e58d49f1b323534e19dafba250d621d37215f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494506"
---
# <a name="displaying-locals"></a>Affichage des variables locales
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [affichant les variables locales](https://docs.microsoft.com/visualstudio/extensibility/debugger/displaying-locals).  
  
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’exécution toujours a lieu dans le contexte d’une méthode, également appelé la méthode conteneur ou la méthode actuelle. Lors de l’exécution s’interrompt, Visual Studio appelle le moteur de débogage (dé) pour obtenir la liste des variables locales et les arguments, appelés collectivement les variables locales de la méthode. Visual Studio affiche ces variables locales et leurs valeurs dans le **variables locales** fenêtre.  
  
 Pour afficher les variables locales, appelle la DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthode appartenant à la EE et lui donne un contexte d’évaluation, qui est, un fournisseur de symboles (SP), l’adresse de l’exécution actuelle et un objet de classeur. Pour plus d’informations, consultez [contexte d’évaluation](../../extensibility/debugger/evaluation-context.md). Si l’appel réussit, la `IDebugExpressionEvaluator::GetMethodProperty` méthode retourne un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui représente la méthode qui contient l’adresse de l’exécution actuelle.  
  
 Les appels DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objet, qui est filtré pour retourner des variables locales uniquement et énumérée pour produire une liste de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)structures. Chaque structure contient le nom, le type et la valeur d’une variable locale. Le type et la valeur sont stockées sous forme de chaînes de mise en forme, qui peut s’afficher. Le nom, le type et la valeur sont généralement affichées ensemble dans une seule ligne de la **variables locales** fenêtre.  
  
> [!NOTE]
>  Le **Espion express** et **espion** fenêtres affichent également des variables avec le même format de nom, valeur et type. Toutefois, ces valeurs sont obtenues en appelant [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) au lieu de `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemple d’implémentation de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Utilise des exemples pas à pas détaillé dans le processus d’implémentation des variables locales.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Explique que lorsque le moteur de débogage (dé) appelle l’évaluateur d’expression (EE), il passe trois arguments.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

