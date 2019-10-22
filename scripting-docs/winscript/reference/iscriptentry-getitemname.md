---
title: 'IScriptEntry :: GetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575464"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Retourne le nom de l’élément qui identifie un objet `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 à Adresse d’une mémoire tampon qui contient le nom de l’élément. Le nom de l’élément est utilisé par l’hôte pour identifier l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Pour les objets `IScriptScriptlet`, vous définissez le nom de l’élément à l’aide de [IActiveScriptAuthor :: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Pour les autres interfaces, vous définissez le nom de l’élément à l’aide de [IScriptEntry :: SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)