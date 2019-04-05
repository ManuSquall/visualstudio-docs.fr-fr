---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5027acbc985ee9afcd8ecd4cf67d2adca40d66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938976"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface marshale les interfaces associées à un programme au-delà des limites de processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface sur le même objet qui implémente [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pour prendre en charge du marshaling d’interfaces au-delà des limites de processus.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un `IDebugProgramNode2` interface pour obtenir cette interface. Si cette interface ne peut pas être obtenue, l’Allemagne ne prend pas en charge le marshaling d’interfaces.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtient une interface spécifiée au-delà des limites de processus.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée lors de l’Allemagne s’exécute dans un espace de processus séparé à partir du programme en cours de débogage : par exemple, lorsque la D’est en cours d’exécution dans l’espace de processus de Visual Studio au lieu de l’espace de processus du programme en cours de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
