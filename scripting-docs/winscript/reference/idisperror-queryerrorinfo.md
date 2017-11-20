---
title: IDispError::QueryErrorInfo | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a165edf2d8f9a0b386daa0035ece1a722401a443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Récupère un type particulier d’informations sur l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le `QueryErrorInfo` méthode récupère un type particulier d’informations sur l’erreur.  
  
> [!NOTE]
>  Cette méthode n’est pas implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)