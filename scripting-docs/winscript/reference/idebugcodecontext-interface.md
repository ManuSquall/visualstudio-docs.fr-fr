---
title: IDebugCodeContext Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext interface
ms.assetid: ae1264d5-1ac2-4b04-9fa5-958212543975
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3d3d1834d176a323778ae9b7d215951d1a26bb4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152575"
---
# <a name="idebugcodecontext-interface"></a>IDebugCodeContext, interface
Une abstraction qui représente une position dans le code exécutable.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugCodeContext` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugCodeContext::GetDocumentContext](../../winscript/reference/idebugcodecontext-getdocumentcontext.md)|Retourne le contexte de document associé à ce contexte de code.|  
|[IDebugCodeContext::SetBreakPoint](../../winscript/reference/idebugcodecontext-setbreakpoint.md)|Définit ou efface un point d’arrêt à ce contexte de code.|