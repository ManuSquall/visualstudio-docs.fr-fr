---
title: 'IScriptEntry :: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c99cda48a20efb41b2535645ccdb50be8bb6d6bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575447"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Pour les entrées qui représentent un seul objet (comme une fonction), retourne le nom de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 à Nom de l’objet représenté par le bloc de script `IScriptEntry`. Si une entrée ne représente pas un seul objet, la valeur NULL est retournée.  
  
 Les entrées enfants représentent un objet de fonction unique.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)