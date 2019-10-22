---
title: 'IScriptScriptlet :: SetEventName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetEventName
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5283646838f02cdc1c5ab27f63fd237d698fc6ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571892"
---
# <a name="iscriptscriptletseteventname"></a>IScriptScriptlet::SetEventName
Définit le nom de l’événement associé au scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 dans Mémoire tampon qui contient le nom de l’événement associé à l’objet `IScriptScriptlet`.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)