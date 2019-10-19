---
title: 'IActiveScript :: GetScriptSite | Microsoft Docs'
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
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575742"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Récupère l’objet de site associé au moteur de script Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iid`  
 dans Identificateur de l’interface demandée.  
  
 `ppvSiteObject`  
 à Adresse de l’emplacement qui reçoit le pointeur d’interface vers l’objet site de l’hôte.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_NOINTERFACE`|L’interface spécifiée n’est pas prise en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`S_FALSE`|Aucun site n’a été défini. le paramètre `ppvSiteObject` a la valeur `NULL`.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)