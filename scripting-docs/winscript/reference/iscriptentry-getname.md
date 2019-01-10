---
title: IScriptEntry::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c388340c35afe2ae7e5e7d0f5078e70b46c0b1bc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090881"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Pour les entrées qui représentent un seul objet (par exemple, une fonction), retourne le nom de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] Le nom de l’objet représenté par le `IScriptEntry` bloc de script. Si une entrée ne représente pas un objet unique, la valeur NULL est retournée.  
  
 Entrées enfants représentent un objet de fonction unique.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [IScriptEntry (Interface)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode :: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)