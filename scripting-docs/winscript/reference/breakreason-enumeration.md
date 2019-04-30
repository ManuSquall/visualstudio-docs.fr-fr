---
title: Énumération BREAKREASON | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955406"
---
# <a name="breakreason-enumeration"></a>Énumération BREAKREASON
Indique ce qui a provoqué l'arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|BREAKREASON_STEP|Le moteur de langage est en mode pas à pas.|  
|BREAKREASON_BREAKPOINT|Le moteur de langage a rencontré un point d’arrêt explicite.|  
|BREAKREASON_DEBUGGER_BLOCK|Le moteur de langage a rencontré un bloc de débogueur sur un autre thread.|  
|BREAKREASON_HOST_INITIATED|L’hôte a demandé une pause.|  
|BREAKREASON_LANGUAGE_INITIATED|Le moteur de langage a demandé une pause.|  
|BREAKREASON_DEBUGGER_HALT|L’IDE de débogueur a demandé une pause.|  
|BREAKREASON_ERROR|Une erreur d’exécution a provoqué l’arrêt.|  
|BREAKREASON_JIT|Dû au démarrage du débogage JIT.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)