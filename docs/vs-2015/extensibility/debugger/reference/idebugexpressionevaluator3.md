---
title: IDebugExpressionEvaluator3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbf159adf4dc475add95ff79d075718b4f5345b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952732"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente un évaluateur d’expression (EE) avec une arborescence d’analyseur améliorée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette version de l’analyseur passe le fournisseur de symboles et l’adresse de l’image de l’évaluation.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interface, cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Convertit une chaîne d’expression en une expression analysée, étant donnée le fournisseur de symboles et l’adresse de l’image de l’évaluation.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : EE.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
