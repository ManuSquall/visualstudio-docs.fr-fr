---
title: IActiveScript::AddTypeLib | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640869"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Ajoute une bibliothèque de types à l’espace de noms pour le script. Ceci est similaire à la `#include` directive en C/C++. Il permet à un ensemble d’éléments prédéfinis, tels que des définitions de classe, `typedefs`et à ajouter à l’environnement d’exécution disponible pour le script de constantes nommées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidTypeLib`  
 [in] CLSID de la bibliothèque de types à ajouter.  
  
 `dwMaj`  
 [in] Numéro de version principale.  
  
 `dwMin`  
 [in] Numéro de version secondaire.  
  
 `dwFlags`  
 [in] Indicateurs d’option. Peut être le suivant :  
  
|Valeur|Signification|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La bibliothèque de types décrit un contrôle ActiveX utilisé par l’hôte.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’était pas valide.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
|`TYPE_E_CANTLOADLIBRARY`|La bibliothèque de types spécifiée n’a pas pu être chargée.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)