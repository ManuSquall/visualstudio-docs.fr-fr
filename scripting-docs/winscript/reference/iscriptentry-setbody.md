---
title: 'IScriptEntry :: SetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575382"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Définit le texte qui se trouve dans le corps d’un `IScriptEntry` bloc de script ou d’un scriptlet `IScriptScriptlet`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 dans Pour un bloc de script `IScriptEntry`, `psz` est le texte placé entre les balises de script.  
  
 Pour un bloc de fonction `IScriptEntry`, `psz` est le corps de la fonction.  
  
 Pour un objet `IScriptScriptlet` (qui dérive de `IScriptEntry`), `psz` est le texte de script du scriptlet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)