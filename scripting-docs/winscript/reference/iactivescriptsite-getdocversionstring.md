---
title: 'IActiveScriptSite :: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571132"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Récupère une chaîne définie par l’hôte qui identifie de façon unique la version du document actuel. Si le document associé a été modifié en dehors de l’étendue de Windows Script (comme dans le cas d’une page HTML en cours de modification avec le bloc-notes), le moteur de script peut l’enregistrer avec son état persistant, en forçant une recompilation lors du chargement suivant du script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrVersionString`  
 à Adresse de la chaîne de version de document définie par l’hôte.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_NOTIMPL` si cette méthode n’est pas prise en charge.  
  
## <a name="remarks"></a>Notes  
 Si `E_NOTIMPL` est retourné, le moteur de script doit supposer que le script est synchronisé avec le document.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)