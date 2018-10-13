---
title: IDebugQueryEngine2 | Microsoft Docs
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
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 747457a93c7cd4da5efe305b0d7f07432fd880b2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307573"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface permet à la session de débogage manager (SDM) extraire une interface qui représente le moteur de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le D’implémente cette interface sur les objets qui implémentent les interfaces DE courants (tels que [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), et [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) dans afin d’autoriser l’accès à la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface de la DE lui-même.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur une interface DE type pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugQueryEngine2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtient une interface de (dé) de moteur de débogage personnalisé.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est généralement implémentée dans l’objet qui implémente le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface pour prendre en charge de la causalité ordonné parcourant des fonctions ; autrement dit, lorsque le débogueur est sortir pas à une fonction, le Pour exécuter la fonction Next peut-être pas la fonction précédente sur la pile, mais une fonction dans un autre thread complètement. Pour une définition de « causalité », consultez la [glossaire du débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

