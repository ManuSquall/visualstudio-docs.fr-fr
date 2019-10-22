---
title: 'IDebugStackFrameSniffer :: EnumStackFrames | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSniffer.EnumStackFrames
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSniffer::EnumStackFrames
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01a2eab1698cd98130b496e58a74cdfdd091efd3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576724"
---
# <a name="idebugstackframesnifferenumstackframes"></a>IDebugStackFrameSniffer::EnumStackFrames
Retourne un énumérateur des frames de pile pour le thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppedsf`  
 à Énumérateur des frames de pile pour le thread actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 L’énumérateur de frame de pile retourne les frames en commençant par le haut de la pile, en commençant par le dernier frame ayant fait l’objet d’un push.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)