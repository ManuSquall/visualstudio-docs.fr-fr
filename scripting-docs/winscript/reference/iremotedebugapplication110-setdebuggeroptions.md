---
title: 'IRemoteDebugApplication110 :: SetDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577422"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Appelé pour mettre à jour les options du débogueur. Cette méthode doit être appelée après [IRemoteDebugApplication :: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). La méthode [IRemoteDebugApplication ::D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) réinitialise automatiquement les options par défaut. La valeur par défaut de l’option est 0 (SDO_NONE).  
  
> [!IMPORTANT]
> L' [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) est implémentée par PDM v 11.0 et ultérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mask`  
 Masque d' [énumération SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 Valeur d' [énumération SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)