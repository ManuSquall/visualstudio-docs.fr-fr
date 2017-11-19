---
title: IRemoteDebugApplicationEx:SetLocale | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEx:SetLocale
apilocation: scrobj.dll
helpviewer_keywords: IRemoteDebugApplicationEx:SetLocale
ms.assetid: cd19f725-f4cd-453a-95e1-0bad676451da
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19b2d58974e7da7bd40dad1faa9e361b0327e4c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationexsetlocale"></a>IRemoteDebugApplicationEx:SetLocale
Définit la langue pour la localisation du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetLocale(  
   DWORD  dwLangID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwLangID`  
 [in] L’ID de langue.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)