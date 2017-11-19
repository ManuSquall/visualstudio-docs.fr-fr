---
title: IActiveScript::SetScriptSite | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informe le moteur de script de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) site interface fournie par l’hôte. Appelez cette méthode avant toute autre [IActiveScript](../../winscript/reference/iactivescript.md) méthodes d’interface est utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pScriptSite`  
 [in] Adresse du site à associer à cette instance du moteur de script fourni par l’hôte de script. Le site doit être attribué de manière unique cette instance du moteur de script ; Il ne peut pas être partagé avec d’autres moteurs de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_FAIL`|Une erreur non spécifiée s’est produite ; le moteur de script n’a pas pu terminer l’initialisation du site.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, un site a déjà été défini).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)