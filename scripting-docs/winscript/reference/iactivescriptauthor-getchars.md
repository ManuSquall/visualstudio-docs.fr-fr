---
title: IActiveScriptAuthor::GetChars | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 69cdeb16fa0791b3ff8c0cce4a4e67fe110eefc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935371"
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
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Demande l’énumération du côté gauche.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Demande le contexte de saisie semi-automatique de membre.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Demande la liste de paramètres.|  
|SCRIPT_CMPL_COMMIT|0x0004|Achèvement de demandes de la liste de paramètres.|  
  
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