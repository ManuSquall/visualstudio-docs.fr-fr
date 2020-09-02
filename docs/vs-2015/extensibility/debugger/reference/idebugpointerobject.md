---
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4cd84c3580d94491e09ce9e8cde8175f9e437be0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693397"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente un objet pointeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 L’évaluateur d’expression implémente cette interface pour représenter un objet pointeur.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 L’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) peut obtenir cette interface en utilisant [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) si le `IDebugObject` représente un pointeur.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 En plus des méthodes héritées de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), l' `IDebugPointerObject` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtient l’objet vers lequel pointe l’interface.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtient la valeur vers laquelle pointe l’interface sous la forme d’une série d’octets consécutifs.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Définit la valeur à laquelle l’interface pointe d’une série d’octets consécutifs.|  
  
## <a name="remarks"></a>Notes  
 Un évaluateur d’expression utilise cette interface pour représenter un pointeur dans une arborescence d’analyse.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : EE. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
