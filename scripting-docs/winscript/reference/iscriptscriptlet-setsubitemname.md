---
title: 'IScriptScriptlet :: SetSubItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab4f7afec9302126ccbfcbe7f2abafc74cbf17d6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571857"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Définit le dernier identificateur dans le nom qualifié complet de l’hôte d’objet d’un scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 Si le nom du scriptlet complet de l’hôte a plusieurs niveaux, `psz` est l’adresse de la mémoire tampon de l’identificateur au deuxième niveau.  
  
 Si le nom du scriptlet complet de l’hôte a un niveau, `psz` est l’adresse de la mémoire tampon de l’identificateur au premier niveau.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)