---
title: IActiveScriptSite::GetDocVersionString | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Récupère une chaîne définie par l’hôte qui identifie de façon unique la version actuelle du document. Si le document associé a été modifié en dehors de Windows Script (comme dans le cas d’une page HTML en cours de modification dans le bloc-notes), le moteur de script pouvez l’enregistrer, ainsi que son état persistant, forcer une recompilation de la prochaine fois que le script est chargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrVersionString`  
 [out] Adresse de la chaîne de version de documents définies par l’hôte.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_NOTIMPL` si cette méthode n’est pas pris en charge.  
  
## <a name="remarks"></a>Remarques  
 Si `E_NOTIMPL` est retourné, le moteur de script doit supposer que le script est synchronisé avec le document.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)