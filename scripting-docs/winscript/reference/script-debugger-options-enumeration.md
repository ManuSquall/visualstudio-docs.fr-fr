---
title: Énumération SCRIPT_DEBUGGER_OPTIONS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e35d90a3750c759282d86c7383bf25204fbf4fcd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088593"
---
# <a name="scriptdebuggeroptions-enumeration"></a>Énumération SCRIPT_DEBUGGER_OPTIONS
Indique un ensemble d’options et/ou les fonctions qui s’appliquent au débogueur joint. Utilisé dans [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) et [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Ces constantes sont implémentées par PDM v10.0 et supérieur. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Value|Description|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Aucune option est définie.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Indique que le runtime de script doit déclencher des événements BREAKREASON_ERROR lorsqu’une exception est levée. Cette option peut être définie par le débogueur, ou par le code utilisateur via `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indique que le débogueur attaché prend en charge les traitements web.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)