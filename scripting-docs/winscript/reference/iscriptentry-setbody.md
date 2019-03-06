---
title: IScriptEntry::SetBody | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 993ffe59abb9458e1b400633430f708e7520599c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088580"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Définit le texte qui se trouve dans le corps d’un `IScriptEntry` bloc de script ou un `IScriptScriptlet` scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 [in] Pour un `IScriptEntry` bloc de script, `psz` est le texte placé entre les balises de script.  
  
 Pour un `IScriptEntry` bloc de fonction, `psz` est le corps de fonction.  
  
 Pour un `IScriptScriptlet` objet (qui dérive à son `IScriptEntry`), `psz` est le texte du script du scriptlet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptEntry (Interface)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)