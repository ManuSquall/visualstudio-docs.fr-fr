---
title: IDebugStackFrame::GetDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDebugProperty
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d3f50029be8489d05c204c57f50c3f7f1326400
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096124"
---
# <a name="idebugstackframegetdebugproperty"></a>IDebugStackFrame::GetDebugProperty
Retourne un Explorateur de propriétés pour le frame actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppDebugProp`  
 [out] Un Explorateur de propriétés pour le frame actuel.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un Explorateur de propriétés pour le frame actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)