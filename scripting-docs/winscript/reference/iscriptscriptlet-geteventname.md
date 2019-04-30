---
title: IScriptScriptlet::GetEventName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetEventName
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56566c85aed88faadf740392ad3ec06aa848431e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786755"
---
# <a name="iscriptscriptletgeteventname"></a>IScriptScriptlet::GetEventName
Retourne le nom de l’événement associé au scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstr`  
 [out] Une mémoire tampon qui contient le nom de l’événement qui est associé le `IScriptScriptlet` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)