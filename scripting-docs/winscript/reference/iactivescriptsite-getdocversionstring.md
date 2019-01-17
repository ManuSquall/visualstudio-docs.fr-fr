---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a451f4883373978772643e11fe22feb9122be30e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349749"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Récupère une chaîne définie par l’hôte qui identifie de façon unique la version actuelle du document. Si le document associé a changé en dehors de la portée de Script Windows (comme dans le cas d’une page HTML en cours de modification avec le bloc-notes), le moteur de script pouvez l’enregistrer, ainsi que son état persistant, en forçant une recompilation, la prochaine fois que le script est chargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrVersionString`  
 [out] Adresse de la chaîne de version de document défini par l’hôte.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite, ou `E_NOTIMPL` si cette méthode n’est pas pris en charge.  
  
## <a name="remarks"></a>Notes  
 Si `E_NOTIMPL` est retourné, le moteur de script doit supposer que le script est synchronisé avec le document.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)