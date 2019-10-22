---
title: 'IScriptScriptlet :: SetSimpleEventName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSimpleEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSimpleEventName
ms.assetid: 7de9132e-635f-45df-9c92-83a24242b477
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47039be628e803b5b5c164b765b0cdf6778621bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571864"
---
# <a name="iscriptscriptletsetsimpleeventname"></a>IScriptScriptlet::SetSimpleEventName
Définit le nom d’événement simple associé à un scriptlet. Il s’agit d’un nom de mot unique qui ne contient aucun espace blanc.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetSimpleEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 dans Mémoire tampon qui contient le nom d’événement simple associé à l’objet `IScriptScriptlet`.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)