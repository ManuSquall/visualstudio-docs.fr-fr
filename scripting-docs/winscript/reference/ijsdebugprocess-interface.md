---
title: Ijsdebugprocess, Interface | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a81104f51ca1a66c493779146b7eaa102ea300
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728569"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess, interface
Fournit des routines d’inspecter et de contrôler le processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode IJsDebugProcess::CreateBreakPoint](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Définit le point d’arrêt à la position du document spécifié.|  
|[Méthode IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Méthode de fabrique pour l’Explorateur de pile.|  
|[Méthode IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Place le moteur de script en mode arrêt, entraînant son arrêt sur l’instruction de script suivante.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)