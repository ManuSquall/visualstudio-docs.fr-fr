---
title: Interface IDebugStackFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0834abbedf88b911dd952c1f3928c5da3414abec
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348540"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame, interface
Représente un frame de pile logique sur la pile des threads. Appelez le `IDebugStackFrame::QueryInterface` méthode pour obtenir le `IDebugExpressionContext` interface, ce qui autorise l’expression d’évaluation et de suivi windows.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugStackFrame` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Retourne le contexte de code actuel associé au frame de pile.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Retourne une description courte ou longue textuelle du frame de pile.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Retourne une description courte ou longue textuelle de la langue.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Retourne le thread associé à ce frame de pile.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Retourne un Explorateur de propriétés pour le frame actuel.|