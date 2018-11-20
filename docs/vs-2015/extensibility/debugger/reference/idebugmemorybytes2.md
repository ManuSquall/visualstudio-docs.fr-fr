---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddbe101efe069787bbbb2ad6462c87bc1151c0cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751956"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente les octets de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface pour représenter les octets en mémoire.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) retourne cette interface pour fournir l’accès à la mémoire système. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) et [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) retourner cette interface pour fournir l’accès pour les octets d’un objet.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugMemoryBytes2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lit une séquence d’octets, en commençant à un emplacement donné.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Écrit `dwCount` octets, en commençant à `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtient la taille, en octets, de la mémoire représentée par cette interface.|  
  
## <a name="remarks"></a>Notes  
 Pour les propriétés, un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente un tableau fournit un `IDebugMemoryBytes2` interface pour accéder aux valeurs de ce tableau.  
  
 De Visual Studio **affichage de la mémoire** appels [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) pour récupérer un `IDebugMemoryBytes2` interface pour accéder à la mémoire système. L’adresse accessible est obtenue par l’analyse de l’expression entrée en tant qu’adresse dans la vue de la mémoire, puis d’évaluer l’expression analysée à l’aide [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir un `IDebugProperty2` interface. Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) retourne le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) décrivant l’adresse mémoire. Ce contexte de la mémoire est ensuite transmis à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

