---
title: Énumération BREAKPOINT_STATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c56a8b135a0aa9a4f8ddf91e146d4d64367bb2b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572638"
---
# <a name="breakpoint_state-enumeration"></a>Énumération BREAKPOINT_STATE
Indique l'état d'un point d'arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Le point d’arrêt n’existe plus, mais il y a toujours des références à celui-ci.|  
|BREAKPOINT_DISABLED|Le point d’arrêt existe mais est désactivé.|  
|BREAKPOINT_ENABLED|Le point d’arrêt existe et est activé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)