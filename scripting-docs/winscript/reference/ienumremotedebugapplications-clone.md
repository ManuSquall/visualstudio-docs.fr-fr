---
title: IEnumRemoteDebugApplications::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Clone
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91f9b9a1461fbf1e87094fea3c908b5afd52ab1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089820"
---
# <a name="ienumremotedebugapplicationsclone"></a>IEnumRemoteDebugApplications::Clone
Crée un énumérateur qui contient le même état que l’énumérateur en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppessd`  
 [out] Un clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un énumérateur qui contient le même état que l’énumérateur en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)