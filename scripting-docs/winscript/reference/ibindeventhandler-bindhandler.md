---
title: IBindEventHandler::BindHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 62ac6de8342f0a436d984f4194351507fdcd5edd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090712"
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
 [in] Spécifie l’événement à gérer.  
  
 `pdisp`  
 [in] Spécifie l’objet pour gérer l’événement.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode lie un événement à un objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)