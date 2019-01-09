---
title: Méthode IJsDebugFrame::GetStackRange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090283"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange, méthode
Retourne la plage d’adresse absolue du frame de pile JavaScript logique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStart`  
 [out] En bas de la plupart des pointeur de pile du frame.  
  
 `pEnd`  
 [out] Supérieur à la plupart des pointeur de pile du frame.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utile pour rassembler des traces de pile entrelacées issues de plusieurs runtimes. Le Guide de démarrage, les pointeurs de pile de fin peuvent englober plusieurs frames de pile d’ordinateur physique (pour les frames d’exécution JavaScript interprétés). Démarrer > mettre fin à mesure que la pile se développe d’élevé à l’adresse basse.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)