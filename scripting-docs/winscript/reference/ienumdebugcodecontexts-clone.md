---
title: IEnumDebugCodeContexts::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Clone
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bdf003c73dd6f98f6f102f3b7dd36b1d69a522c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089529"
---
# <a name="ienumdebugcodecontextsclone"></a>IEnumDebugCodeContexts::Clone
Crée un énumérateur qui contient le même état que l’énumérateur en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppescc`  
 [out] Retourne le `IEnumDebugCodeContexts` interface du clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un énumérateur qui contient le même état que l’énumérateur en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)