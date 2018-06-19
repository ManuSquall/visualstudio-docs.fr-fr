---
title: IActiveScriptErrorDebug (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645749"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug, interface
Fournit des informations de contexte de document pour les erreurs de compilation et des exceptions d’exécution. Le `IActiveScriptError::QueryInterface` prend en charge de la méthode la `IActiveScriptErrorDebug` interface.  
  
 Outre les méthodes héritées de `IActiveScriptError`, le `IActiveScriptErrorDebug` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fournit le contexte de document pour cette erreur.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fournit le frame de pile qui est appliquée pour les erreurs d’exécution.|