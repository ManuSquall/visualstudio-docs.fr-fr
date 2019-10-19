---
title: 'IJsDebugFrame :: GetStackRange,, méthode | Microsoft Docs'
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
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574043"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange, méthode
Retourne la plage d’adresses absolue du frame de pile JavaScript logique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStart`  
 à Pointeur de pile le plus bas du frame.  
  
 `pEnd`  
 à Pointeur le plus haut de la pile du frame.  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utile pour accolant ensemble des traces de pile entrelacées rassemblées à partir de plusieurs runtimes. Les pointeurs de pile de début et de fin peuvent englober plusieurs frames de pile d’ordinateur physique (pour les frames de Runtime JavaScript interprétés). Démarrer > fin à mesure que la pile augmente d’une adresse de haut en bas.  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)