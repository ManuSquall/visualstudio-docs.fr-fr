---
title: 'IActiveScript :: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575795"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clone le moteur de script actuel (moins tout état d’exécution en cours), en retournant un moteur de script chargé qui n’a pas de site dans le thread actuel. Les propriétés de ce nouveau moteur de script seront identiques à celles du moteur de script d’origine, s’il était passé à l’état initialisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppscript`  
 à Adresse d’une variable qui reçoit un pointeur vers l’interface [IActiveScript](../../winscript/reference/iactivescript.md) du moteur de script cloné. L’hôte doit créer un site et appeler la méthode [IActiveScript :: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) sur le nouveau moteur de script avant qu’il ne soit dans l’état initialisé et, par conséquent, utilisable.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Notes  
 La méthode `IActiveScript::Clone` est une optimisation de `IPersist*::Save`, `CoCreateInstance` et `IPersist*::Load`, donc l’état du nouveau moteur de script doit être le même que si l’état du moteur de script d’origine était enregistré et chargé dans un nouveau moteur de script. Les éléments nommés sont dupliqués dans le moteur de script cloné, mais les pointeurs d’objets spécifiques pour chaque élément sont oubliés et sont obtenus avec la méthode [IActiveScriptSite :: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . Cela permet d’utiliser un modèle d’objet identique avec des points d’entrée par thread (modèle Apartment).  
  
 Cette méthode est utilisée pour les hôtes de serveur multithread qui peuvent exécuter plusieurs instances du même script. Le moteur de script peut retourner `E_NOTIMPL`, auquel cas l’hôte peut obtenir le même résultat en dupliquant l’état persistant et en créant une nouvelle instance du moteur de script avec une interface `IPersist*`.  
  
 Cette méthode peut être appelée à partir de threads non de base sans aboutir à un appel de non-base pour héberger des objets ou à l’interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)