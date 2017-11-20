---
title: IActiveScriptAuthor::GetChars | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Retourne le jeu de caractères de fin pour un contexte d’exécution demandé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fRequestedList`  
 [in] Le contexte d’exécution demandée.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0 x 0001|Demande l’énumération du côté gauche.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0 x 0002|Demande le contexte d’exécution de membre.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0 x 0003|Demande la liste de paramètres.|  
|SCRIPT_CMPL_COMMIT|0 x 0004|Exécution de requêtes de la liste de paramètres.|  
  
 `pbstrChars`  
 [out] Les caractères qui correspondent au contexte de l’achèvement demandée.  
  
|`fRequestedList`paramètre|Caractères retournés|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)