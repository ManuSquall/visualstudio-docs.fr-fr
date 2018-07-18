---
title: Ijsdebugdatatarget::createstackframeenumerator, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation:
- jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91c67dc3eb14217ffcdc41f0877df6837fcb0230
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727499"
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>IJsDebugDataTarget::CreateStackFrameEnumerator, méthode
Crée un énumérateur pour les frames de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadId`  
 [in] Thread en cours d’exécution dans le processus cible.  
  
 `ppEnumerator`  
 [out] L’énumérateur pour les frames de pile.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)