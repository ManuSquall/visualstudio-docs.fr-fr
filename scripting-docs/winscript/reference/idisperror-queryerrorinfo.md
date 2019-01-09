---
title: IDispError::QueryErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01c33ab9ef187f5bf9d6146e23c4534a33844cec
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091778"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Récupère un type particulier d’informations d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidErrorType`  
 [in] Type d’erreur en spécifiant GUID.  
  
 `ppde`  
 [out] Spécifie l’objet IDispError.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le `QueryErrorInfo` méthode récupère un type particulier d’informations d’erreur.  
  
> [!NOTE]
>  Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)