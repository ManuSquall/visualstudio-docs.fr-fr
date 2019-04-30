---
title: Interface IJsDebugProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 411679a03daf27046fdcede7ff48e76212bbd2fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557944"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess, interface
Fournit des routines pour inspecter et contrôler le processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode IJsDebugProcess::CreateBreakPoint](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Définit le point d’arrêt à la position du document spécifié.|  
|[Méthode IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Méthode de fabrique pour l’Explorateur de pile.|  
|[Méthode IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Place le moteur de script en mode arrêt, ce qui provoque son arrêt sur l’instruction de script suivante.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)