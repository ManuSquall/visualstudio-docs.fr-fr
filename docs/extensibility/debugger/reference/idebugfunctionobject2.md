---
title: IDebugFunctionObject2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bbf52230b93357e85326f868254cf1d5c5a9dbb9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Représente une fonction et améliore la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Évaluateur d’expression (EE) implémente cette interface pour représenter une fonction.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Méthodes de cette interface différeront de ceux de **IDebugFunctionObject** comme suit :  
  
-   Le **IDebugEvaluate** méthode utilise les indicateurs.  
  
-   Le **CreateObject** méthode prend un délai d’attente et les indicateurs.  
  
-   Le **CreateStringObjectWithLength** méthode prend une longueur.  
  
## <a name="methods"></a>Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crée un objet qui utilise un constructeur de fonction de paramètres d’évaluation de l’indicateur et une valeur de délai d’attente.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crée un objet de chaîne qui a la longueur spécifiée.|  
|[Évaluer](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Appelle la fonction et retourne la valeur obtenue en tant qu’objet.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll