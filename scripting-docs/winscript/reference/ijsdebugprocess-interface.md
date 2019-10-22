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
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577347"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess, interface
Fournit des routines pour l’inspection et le contrôle du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[Méthode IJsDebugProcess::CreateBreakPoint](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Définit le point d’arrêt à la position de document spécifiée.|  
|[Méthode IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Méthode de fabrique pour l’Explorateur de piles.|  
|[Méthode IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Met le moteur de script en mode arrêt, provoquant l’arrêt de l’instruction de script suivante.|  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)