---
title: 'IActiveScriptSite :: GetLCID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570738"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Récupère l’identificateur de paramètres régionaux associé à l’interface utilisateur de l’hôte. Le moteur de script utilise l’identificateur pour s’assurer que les chaînes d’erreur et autres éléments d’interface utilisateur générés par le moteur s’affichent dans la langue appropriée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `plcid`  
 à Adresse d’une variable qui reçoit l’identificateur de paramètres régionaux pour les éléments de l’interface utilisateur affichés par le moteur de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_NOTIMPL`|Cette méthode n’est pas implémentée. Utilisez les paramètres régionaux définis par le système.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
  
## <a name="remarks"></a>Notes  
 Si cette méthode retourne `E_NOTIMPL`, l’identificateur de paramètres régionaux défini par le système doit être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)