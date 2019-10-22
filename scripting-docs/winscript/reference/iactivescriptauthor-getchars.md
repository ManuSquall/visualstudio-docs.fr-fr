---
title: 'IActiveScriptAuthor :: GetChars | Microsoft Docs'
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
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576253"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Retourne le jeu de caractères de saisie semi-automatique pour un contexte de saisie semi-automatique demandé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fRequestedList`  
 dans Contexte d’achèvement demandé.  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Demande l’énumération côté gauche.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Demande le contexte de saisie semi-automatique de membre.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Demande la liste de paramètres.|  
|SCRIPT_CMPL_COMMIT|0x0004|Demande la saisie semi-automatique de la liste de paramètres.|  
  
 `pbstrChars`  
 à Caractères qui correspondent au contexte de saisie semi-automatique demandé.  
  
|paramètre `fRequestedList`|Caractères retournés|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)