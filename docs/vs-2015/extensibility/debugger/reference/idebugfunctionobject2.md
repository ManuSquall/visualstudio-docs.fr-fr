---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9aa191d36c057e2d5cdcd1c551ac96f6804738b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953109"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente une fonction et améliore la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un évaluateur d’expression (EE) implémente cette interface pour représenter une fonction.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Méthodes de cette interface différeront de ceux de **IDebugFunctionObject** comme suit :  
  
-   Le **IDebugEvaluate** méthode accepte des indicateurs.  
  
-   Le **CreateObject** méthode accepte des indicateurs et un délai d’expiration.  
  
-   Le **CreateStringObjectWithLength** méthode prend une longueur.  
  
## <a name="methods"></a>Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crée un objet qui utilise un constructeur étant donné les paramètres de l’indicateur d’évaluation et une valeur de délai d’attente.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crée un objet de chaîne qui a la longueur spécifiée.|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Appelle la fonction et retourne la valeur obtenue en tant qu’objet.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : EE.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
