---
title: Implémentation d’un évaluateur d’Expression | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b32ae1580ccba207f7d5e86fc4ac48d38fec7fbf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786832"
---
# <a name="implementing-an-expression-evaluator"></a>Implémentation d’un évaluateur d’expression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Évaluation d’une expression est une interaction complexe entre le moteur de débogage (dé), le fournisseur de symboles (SP), l’objet de classeur et l’évaluateur d’expression (EE) lui-même. Ces quatre composants sont connectés par les interfaces qui sont implémentées par un composant et consommées par un autre.  
  
 Le EE prend une expression à partir de l’Allemagne sous la forme d’une chaîne et analyse ni n’évalue. Le EE implémente les interfaces suivantes, qui sont consommés par le DE :  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  Le EE appelle l’objet de classeur, fourni par l’Allemagne, pour obtenir la valeur des symboles et des objets. Le EE consomme les interfaces suivantes, qui sont implémentées par le DE :  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Implémente le EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fournit le mécanisme permettant de décrire le résultat d’une évaluation d’expression, tel qu’une variable locale, une primitive ou un objet, à Visual Studio, il affiche ensuite les informations appropriées dans le **variables locales**,  **Espion**, ou **immédiat** fenêtre.  
  
  La procédure stockée est fournie pour le EE par le DE lorsqu’il demande d’informations. La procédure stockée implémente les interfaces qui décrivent les adresses et les champs, tels que les interfaces suivantes et leurs dérivés :  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  Le EE consomme toutes ces interfaces.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Stratégie d’implémentation d’un évaluateur d’expression](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Définit un processus en trois étapes pour la stratégie d’implémentation expression évaluateur (EE).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

