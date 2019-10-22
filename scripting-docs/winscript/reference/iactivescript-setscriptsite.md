---
title: 'IActiveScript :: SetScriptSite | Microsoft Docs'
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
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575330"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informe le moteur de script du site d’interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fourni par l’hôte. Appelez cette méthode avant d’utiliser d’autres méthodes d’interface [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pScriptSite`  
 dans Adresse du site de script fourni par l’hôte à associer à cette instance du moteur de script. Le site doit être attribué de manière unique à cette instance du moteur de script. il ne peut pas être partagé avec d’autres moteurs de script.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_FAIL`|Une erreur non spécifiée s’est produite. le moteur de script n’a pas pu terminer l’initialisation du site.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, un site a déjà été défini).|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)