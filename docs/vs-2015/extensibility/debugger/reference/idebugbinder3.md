---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f23c2ad4aeaf911e45b28686584d741e5c4d22f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704136"
---
# <a name="idebugbinder3"></a>IDebugBinder3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit l’accès aux types, aux alias et aux services de visualiseur personnalisés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un moteur de débogage implémente cette interface pour prendre en charge les alias, les services de visualiseur personnalisés et l’accès aux informations sur le type d’objet.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Une interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obtient cette interface à l’aide de [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable  
 Outre les méthodes fournies par l’interface [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , cette interface implémente les éléments suivants :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Récupère un objet mémoire représentant la mémoire à laquelle cet objet est lié.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Récupère l’exception associée à cet objet (le cas échéant),|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Récupère un alias en fonction de son nom,|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Récupère un tableau de tous les alias pour cet objet,|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtient le nombre de types d’arguments associés à cet objet.|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Récupère une liste de types d’arguments associés à cet objet.|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtient une interface pour un service de visualiseur,|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convertit l’emplacement d’un objet ou une adresse mémoire 64 bits en un contexte de mémoire.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : EE. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
