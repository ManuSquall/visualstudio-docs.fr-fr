---
title: IActiveScriptSite::GetLCID | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Récupère l’identificateur de paramètres régionaux liée à l’interface utilisateur de l’ordinateur hôte. Le moteur de script utilise l’identificateur pour vous assurer que les chaînes d’erreur et d’autres éléments d’interface utilisateur générées par le moteur s’affichent dans la langue appropriée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `plcid`  
 [out] Adresse d’une variable qui reçoit l’identificateur de paramètres régionaux pour les éléments d’interface utilisateur affichée par le moteur de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_NOTIMPL`|Cette méthode n’est pas implémentée. Utilisez les paramètres régionaux définis par le système.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
  
## <a name="remarks"></a>Remarques  
 Si cette méthode retourne `E_NOTIMPL`, l’identificateur défini par le système doit être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)