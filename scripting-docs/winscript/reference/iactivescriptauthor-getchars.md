---
title: IActiveScriptAuthor::GetChars | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e7a7cf276e589aaaa3c00ecab8cbf881942f82
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094326"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Retourne le jeu de caractères de saisie semi-automatique pour un contexte d’exécution demandée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fRequestedList`  
 [in] Le contexte de la saisie semi-automatique demandée.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0 x 0001|Demande l’énumération du côté gauche.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0 x 0002|Demande le contexte de saisie semi-automatique de membre.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Demande la liste de paramètres.|  
|SCRIPT_CMPL_COMMIT|0 x 0004|Achèvement de demandes de la liste de paramètres.|  
  
 `pbstrChars`  
 [out] Les caractères qui correspondent au contexte de l’achèvement demandée.  
  
|`fRequestedList` Paramètre|Caractères retournés|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)