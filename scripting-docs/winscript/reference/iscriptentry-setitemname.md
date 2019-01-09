---
title: IScriptEntry::SetItemName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20af0975a4175d10b110ac5e3cef9e0055f4ce1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097758"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Définit le nom de l’élément qui identifie un `IScriptEntry` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 [in] L’adresse d’une mémoire tampon qui contient le nom de l’élément. Le nom de l’élément est utilisé par l’hôte pour identifier l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode n’a pas réussi.|  
  
## <a name="remarks"></a>Notes  
 Pour `IScriptEntry` objets, cette méthode retourne `S_OK`.  
  
 Pour `IScriptScriptlet` objets (qui dérivent de `IScriptEntry`), cette méthode retourne `E_FAIL`. Pour `IScriptScriptlet` objets, le nom de l’élément est défini [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) et ne peut pas être modifié.  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptEntry (Interface)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)