---
title: 'IScriptScriptlet :: GetSubItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b36f6dd98534b8122a6814f1fd154eca7882251a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571920"
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Retourne le dernier identificateur dans le nom qualifié complet de l’hôte d’objet d’un scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 à Si le nom du scriptlet complet de l’hôte a plusieurs niveaux, `pbstr` retourne l’adresse de la mémoire tampon de l’identificateur au deuxième niveau.  
  
 Si le nom du scriptlet complet de l’hôte a un niveau, `pbstr` retourne l’adresse de la mémoire tampon de l’identificateur au premier niveau.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)