---
title: IEnumRemoteDebugApplications::Clone | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplications.Clone
apilocation: scrobj.dll
helpviewer_keywords: IEnumRemoteDebugApplications::Clone
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97b135d0139be40fa864064422027e7c3247fc8a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationsclone"></a>IEnumRemoteDebugApplications::Clone
Crée un énumérateur qui contient le même état que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppessd`  
 [out] Un clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode crée un énumérateur qui contient le même état que l’énumérateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)