---
title: 'IActiveScript :: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575808"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Ajoute une bibliothèque de types à l’espace de noms pour le script. Cela est similaire à la directive `#include` en C/C++. Il permet à un ensemble d’éléments prédéfinis tels que les définitions de classe, les `typedefs` et les constantes nommées d’être ajoutés à l’environnement d’exécution disponible pour le script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guidTypeLib`  
 dans CLSID de la bibliothèque de types à ajouter.  
  
 `dwMaj`  
 dans Numéro de version principale.  
  
 `dwMin`  
 dans Numéro de version mineure.  
  
 `dwFlags`  
 dans Indicateurs d’option. Il peut s’agir des éléments suivants :  
  
|valeur|Signification|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La bibliothèque de types décrit un contrôle ActiveX utilisé par l’hôte.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
|`TYPE_E_CANTLOADLIBRARY`|Impossible de charger la bibliothèque de types spécifiée.|  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)