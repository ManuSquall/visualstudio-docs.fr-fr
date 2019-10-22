---
title: 'IBindEventHandler :: BindHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBindEventHandler.BindHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 160020832509c9fb2aa95c095148127228a92e17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572570"
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Lie un événement à un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrEvent`  
 dans Spécifie l’événement à gérer.  
  
 `pdisp`  
 dans Spécifie l’objet pour gérer l’événement.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode lie un événement à un objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)