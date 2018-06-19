---
title: IActiveScript::GetScriptSite | Documents Microsoft
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
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640369"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Récupère l’objet de site associé au moteur de Script Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Identificateur de l’interface demandée.  
  
 `ppvSiteObject`  
 [out] Adresse de l’emplacement qui reçoit le pointeur d’interface à l’objet de site de l’ordinateur hôte.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_NOINTERFACE`|L’interface spécifiée n’est pas pris en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`S_FALSE`|Aucun site n’a été défini ; le `ppvSiteObject` paramètre est défini sur `NULL`.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)