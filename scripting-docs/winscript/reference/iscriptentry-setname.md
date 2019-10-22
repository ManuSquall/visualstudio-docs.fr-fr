---
title: 'IScriptEntry :: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetName
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9dfa27c6c8c58c0ee1599e17e1da5b5f424e416
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575355"
---
# <a name="iscriptentrysetname"></a>IScriptEntry::SetName
Pour les entrées qui représentent un seul objet (par exemple, une fonction), définit le nom de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 dans Nouveau nom de l’objet `IScriptEntry`.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)