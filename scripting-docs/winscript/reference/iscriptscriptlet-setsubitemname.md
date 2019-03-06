---
title: IScriptScriptlet::SetSubItemName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 777a69e47ed7f88851cae0d20f2eb23ee6978296
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097711"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Définit le dernier identificateur dans le nom qualifié complet de l’hôte de l’objet d’un scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 Si l’hôte complet de nom de scriptlet a plusieurs niveaux, `psz` est l’adresse du tampon de l’identificateur au deuxième niveau.  
  
 Si l’hôte complet de scriptlet nom a un niveau, `psz` est l’adresse du tampon de l’identificateur du premier niveau.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)