---
title: IDebugMemoryBytes2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a7c7dbc966c6c2747de4c969975ef8455cf6b0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116856"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Cette interface représente les octets de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter les octets dans la mémoire.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) renvoie cette interface pour fournir l’accès à la mémoire système. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) et [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) retourner cette interface pour fournir l’accès pour les octets d’un objet.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugMemoryBytes2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lit une séquence d’octets, en commençant à un emplacement donné.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Écrit `dwCount` octets à partir de `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtient la taille, en octets, de la mémoire représentée par cette interface.|  
  
## <a name="remarks"></a>Notes  
 Pour les propriétés, un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente un tableau fournit une `IDebugMemoryBytes2` interface pour accéder aux valeurs dans ce tableau.  
  
 Visual Studio **affichage de la mémoire** appelle [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) pour récupérer un `IDebugMemoryBytes2` interface pour accéder à la mémoire système. L’adresse accessible est obtenue par l’analyse de l’expression entrée en tant qu’adresse dans la vue de la mémoire, puis d’évaluer l’expression analysée à l’aide de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir un `IDebugProperty2` interface. Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) retourne le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) qui décrit l’adresse mémoire. Ce contexte de la mémoire est ensuite transmis à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)