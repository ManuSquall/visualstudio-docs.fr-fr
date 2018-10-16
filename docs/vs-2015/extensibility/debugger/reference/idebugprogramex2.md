---
title: IDebugProgramEx2 | Microsoft Docs
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
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb8009203a4d97ef5ecce37751495300b3b9248c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241518"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface permet à la session de débogage manager (SDM) attacher à un programme et obtenir le nœud de programme associé à un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface afin de permettre le SDM attacher à un programme, même si en même temps, ce qui permet le fournisseur de port effectuer le suivi de toutes les sessions attaché à la programme. Le fournisseur de port personnalisé peut implémenter cette interface si elle choisit.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les appels SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un `IDebugProgram2` interface pour obtenir cette interface pour effectuer le suivi des sessions qui ont associés à des programmes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProgramEx2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Attacher](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Attache un programme à une session.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtient le nœud de programme associé à un programme.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est privée entre le SDM et le programme.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Portpriv.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

