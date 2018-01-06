---
title: IDebugObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject
helpviewer_keywords: IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1122b427b6678d7f097d424aca0420642fecdbb2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente un objet binder crée pour encapsuler les valeurs de symboles et d’expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Évaluateur d’expression implémente cette interface pour représenter un objet.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est la classe de base pour tous les objets par l’évaluateur d’expression dans les expressions analysées. Il est retourné par un appel à la [lier](../../../extensibility/debugger/reference/idebugbinder-bind.md) méthode. [QueryInterface](/cpp/atl/queryinterface) Obtient les interfaces plus spécialisées à partir de cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugObject`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtient la taille de l’objet.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtient la valeur de l’objet sous la forme d’une série consécutif d’octets.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Définit la valeur de l’objet à partir d’une série consécutif d’octets.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Définit la valeur de référence de cet objet.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtient le contexte de la mémoire qui représente l’adresse de la valeur de l’objet.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crée une copie de l’objet managé dans l’espace d’adressage du moteur de débogage.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Teste si cet objet est une référence null.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compare un objet à celui-ci.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Détermine si cet objet est en lecture seule.|  
|[Proxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Détermine si l’objet est un proxy transparent.|  
  
## <a name="remarks"></a>Notes  
 L’évaluateur d’expression utilise cette interface comme classe de base pour représenter des objets dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)