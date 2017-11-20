---
title: IDebugQueryEngine2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugQueryEngine2
helpviewer_keywords: IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5545d49776e31b60719a49e4dbdca14d7dfdda3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Cette interface permet à la session de débogage responsable de récupérer une interface qui représente le moteur de débogage (DE).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface sur les objets qui implémentent les interfaces DE courants (tels que [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), et [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) dans afin de permettre l’accès à la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface de la DE lui-même.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface DE type pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugQueryEngine2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtient une interface du moteur (DE) de débogage personnalisées.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface est généralement implémentée dans l’objet qui implémente le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface pour prendre en charge de la causalité ordonné pas à pas via des fonctions, autrement dit, lorsque le débogueur est sortir pas à une fonction, le Pour exécuter la fonction Next peut-être pas la fonction précédente sur la pile, mais une fonction dans un autre thread complètement. Pour une définition de « causalité », consultez la [glossaire de débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)