---
title: 'IScriptEntry :: SetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575369"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Définit le nom de l’élément qui identifie un objet `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 dans Adresse d’une mémoire tampon qui contient le nom de l’élément. Le nom de l’élément est utilisé par l’hôte pour identifier l’entrée.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode n’a pas pu être effectuée.|  
  
## <a name="remarks"></a>Notes  
 Pour les objets `IScriptEntry`, cette méthode retourne `S_OK`.  
  
 Pour les objets `IScriptScriptlet` (qui dérivent de `IScriptEntry`), cette méthode retourne `E_FAIL`. Pour les objets `IScriptScriptlet`, le nom de l’élément est défini par [IActiveScriptAuthor :: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) et ne peut pas être modifié.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)