---
title: Énumération SCRIPT_DEBUGGER_OPTIONS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574565"
---
# <a name="script_debugger_options-enumeration"></a>Énumération SCRIPT_DEBUGGER_OPTIONS
Indique un ensemble d’options et/ou de fonctionnalités qui s’appliquent au débogueur attaché. Utilisé dans [IDebugApplicationNode100 :: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) et [IDebugApplicationNode100 :: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Ces constantes sont implémentées par PDM v 10.0 et versions ultérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Membres  
  
|Membre|valeur|Description|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Aucune option n’est définie.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Indique que l’exécution du script doit déclencher des événements BREAKREASON_ERROR lorsqu’une exception est levée. Cette option peut être définie par le débogueur, ou définie par le code utilisateur via `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indique que le débogueur attaché prend en charge les traitements Web.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)