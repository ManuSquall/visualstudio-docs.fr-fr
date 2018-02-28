---
title: IScriptEntry::GetItemName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdbb293afc6f58f8d9d9c1fe27bae467fd36792c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Retourne le nom de l’élément qui identifie un `IScriptEntry` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] L’adresse d’une mémoire tampon qui contient le nom de l’élément. Le nom de l’élément est utilisé par l’hôte pour identifier l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Pour `IScriptScriptlet` des objets, vous définissez le nom de l’élément à l’aide de [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Pour les autres interfaces, vous définissez le nom de l’élément à l’aide de [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)