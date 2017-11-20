---
title: "Ijsdebugprocess::createstackwalker, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ca7594f4e3c6ef44aa8cde1d92f17d46a9aa30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker, méthode
Méthode de fabrique pour l’Explorateur de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 [in] L’ID de thread.  
  
 `ppStackWalker`  
 [out] Le nouvel objet walker de pile.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Retourne E_JsDEBUG_UNKNOWN_THREAD si le thread n’a pas de JavaScript sur celui-ci. Cette méthode peut être appelée uniquement pendant que le processus cible est arrêté.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)