---
title: IEnumDebugStackFrames::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 978a96fdb08c460ead1b09bdc20ef6a8cf886c57
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093806"
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
Crée un énumérateur qui contient le même état que l’énumérateur en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppedsf`  
 [out] Retourne le `IEnumDebugStackFrames` interface du clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un énumérateur qui contient le même état que l’énumérateur en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)