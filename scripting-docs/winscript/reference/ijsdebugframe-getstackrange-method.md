---
title: Méthode IJsDebugFrame::GetStackRange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 52dd6114d3ec462f91f8bce5e76f73c5487746ed
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147434"
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