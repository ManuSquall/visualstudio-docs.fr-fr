---
title: IScriptNode::GetCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetCookie
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetCookie
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05d184af3ecd6302fc05893600fd7026eeca3ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787051"
---
# <a name="iscriptnodegetcookie"></a>IScriptNode::GetCookie
Retourne une valeur définie par l’application qui est utilisée pour associer un scriptlet à l’objet hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwCookie`  
 [out] Pour un `IScriptEntry` d’objet, retourne la valeur du cookie définie par l’application.  
  
 Pour un `IScriptNode` objet qui représente une page Web, retourne 0.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)