---
title: IActiveScript::GetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b57c4282b7ec77eb4af2ffa983479ae77388e1c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935769"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Récupère l’objet de site associé avec le moteur de Script de Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Identificateur de l’interface demandée.  
  
 `ppvSiteObject`  
 [out] Adresse de l’emplacement qui reçoit le pointeur d’interface à l’objet de site de l’hôte.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_NOINTERFACE`|L’interface spécifiée n’est pas pris en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`S_FALSE`|Aucun site n’a été définie ; le `ppvSiteObject` paramètre est défini sur `NULL`.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)