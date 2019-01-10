---
title: IActiveScript::GetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 85b7d94ccb9e2589b10bf705721fc289df9638a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094157"
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