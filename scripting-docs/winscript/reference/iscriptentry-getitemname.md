---
title: IScriptEntry::GetItemName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4fc82dbd26fc2b9956b3d32596e5fa730b96f9a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093455"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Retourne le nom de l’élément qui identifie un `IScriptEntry` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] L’adresse d’une mémoire tampon qui contient le nom de l’élément. Le nom de l’élément est utilisé par l’hôte pour identifier l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Pour `IScriptScriptlet` objets, vous définissez le nom de l’élément à l’aide de [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Pour les autres interfaces, vous définissez le nom de l’élément à l’aide de [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)