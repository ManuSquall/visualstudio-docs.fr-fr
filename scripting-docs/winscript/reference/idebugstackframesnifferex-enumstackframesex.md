---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Retourne un énumérateur de frames de pile du thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSpMin`  
 [in] La limite inférieure d’adresse pour l’énumération des frames de pile.  
  
 `ppedsf`  
 [out] Énumérateur des frames de pile du thread actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 L’énumérateur de frame de pile retourne les frames en haut de la pile, avec le plus récemment envoyée frame. L’énumérateur contient uniquement les frames de pile avec des adresses supérieurs ou égales à `dwSpMin`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)