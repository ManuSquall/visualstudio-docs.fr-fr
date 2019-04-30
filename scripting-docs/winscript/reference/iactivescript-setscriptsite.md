---
title: IActiveScript::SetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935552"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informe le moteur de script de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) site interface fournie par l’hôte. Appelez cette méthode avant toute autre [IActiveScript](../../winscript/reference/iactivescript.md) méthodes d’interface est utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pScriptSite`  
 [in] Adresse du site de script fourni par l’hôte à associer à cette instance du moteur de script. Le site doit être attribué de manière unique cette instance du moteur de script ; Il ne peut pas être partagé avec d’autres moteurs de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_FAIL`|Une erreur non spécifiée s’est produite ; le moteur de script n’a pas pu terminer l’initialisation du site.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, un site a déjà été défini).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)