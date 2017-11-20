---
title: IDebugExpressionContext (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext Interface
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext interface
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c55a2f270e4c82c578450092e5066b19fe9e606
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontext-interface"></a>IDebugExpressionContext, interface
Représente un contexte où les expressions peuvent être évaluées. L’objet de frame de pile implémente cette interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugExpressionContext` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Crée une expression de débogage pour le texte spécifié.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Retourne un nom et un GUID pour la langue qui possède ce contexte.|