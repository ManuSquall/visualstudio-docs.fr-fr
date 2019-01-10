---
title: IScriptScriptlet::SetEventName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 10accabb3ca4e070173530cba3c60da9d7e5bb04
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092051"
---
# <a name="iscriptscriptletseteventname"></a>IScriptScriptlet::SetEventName
Définit le nom de l’événement qui est associé avec le scriptlet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 [in] Une mémoire tampon qui contient le nom de l’événement qui est associé le `IScriptScriptlet` objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)