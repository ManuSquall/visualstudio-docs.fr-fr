---
title: IActiveScript::Clone | Microsoft Docs
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
ms.openlocfilehash: bec912596c792a67f65434062bc0d0ed11bd3fb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935703"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clone le moteur de script actuel (moins de n’importe quel état d’exécution actuel), retournant un moteur de script chargé qui ne possède aucun site dans le thread actuel. Les propriétés de ce nouveau moteur de script seront identiques à celles que du moteur de script d’origine se trouverait dans si elle a été transmise à l’état initialisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppscript`  
 [out] Adresse d’une variable qui reçoit un pointeur vers le [IActiveScript](../../winscript/reference/iactivescript.md) interface du moteur de script cloné. L’hôte doit créer un site et l’appel de la [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) méthode sur le nouveau moteur de script avant d’être dans l’état initialisé et, par conséquent, utilisable.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Notes  
 Le `IActiveScript::Clone` méthode est une optimisation de `IPersist*::Save`, `CoCreateInstance`, et `IPersist*::Load`, de sorte que l’état du nouveau moteur de script doit être le même que si l’état du moteur de script d’origine ont été enregistrée et chargée dans un nouveau moteur de script. Éléments nommés sont dupliquées dans le moteur de script cloné, mais les pointeurs d’objet spécifique pour chaque élément oubliées et peuvent être obtenues avec le [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) (méthode). Ainsi, un modèle d’objet identiques avec des points d’entrée par thread (un modèle de cloisonnement) à utiliser.  
  
 Cette méthode est utilisée pour les hôtes de serveur multithread qui peuvent exécuter plusieurs instances du même script. Le moteur de script peut retourner `E_NOTIMPL`, auquel cas l’hôte peut obtenir le même résultat en dupliquant l’état permanent et en créant une nouvelle instance du moteur de script avec un `IPersist*` interface.  
  
 Cette méthode peut être appelée à partir de threads de base autre sans résultant dans une légende de base autre à des objets de l’hôte ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)