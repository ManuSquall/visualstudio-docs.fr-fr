---
title: "Ijsdebugframe::GetStackRange, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange, méthode
Retourne la plage d’adresses absolues du frame de pile JavaScript logique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStart`  
 [out] En bas de la plupart des pointeur de pile du frame.  
  
 `pEnd`  
 [out] Supérieur à la plupart des pointeur bac de réception de l’image.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est utile pour regrouper des traces de pile entrelacées issues de plusieurs runtimes. Début, fin les pointeurs de pile peuvent englober plusieurs frames de pile de l’ordinateur physique (pour les images du runtime JavaScript interprétés). Démarrer > fur et à la pile d’élevé à basse adresse de fin.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)