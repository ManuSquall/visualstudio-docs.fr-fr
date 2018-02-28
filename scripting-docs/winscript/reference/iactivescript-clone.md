---
title: IActiveScript::Clone | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clone le moteur de script actuel (moins de n’importe quel état d’exécution actuel), retournant un moteur de script chargé qui ne possède aucun site dans le thread actuel. Les propriétés de ce nouveau moteur de script seront identiques à celles que du moteur de script d’origine serait dans si elle a été passée à l’état initialisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppscript`  
 [out] Adresse d’une variable qui reçoit un pointeur vers le [IActiveScript](../../winscript/reference/iactivescript.md) interface du moteur de script cloné. L’hôte doit créer un site et l’appel de la [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) méthode sur le nouveau moteur de script avant d’être dans l’état initialisé et, par conséquent, utilisable.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Remarques  
 Le `IActiveScript::Clone` méthode est une optimisation des `IPersist*::Save`, `CoCreateInstance`, et `IPersist*::Load`, de sorte que l’état du nouveau moteur de script doit être le même que si l’état du moteur de script d’origine ont été enregistrée et chargée dans un nouveau moteur de script. Éléments nommés sont dupliquées dans le moteur de script cloné, mais les pointeurs d’objet spécifique pour chaque élément sont oubliés et sont obtenus par le [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) (méthode). Cela permet à un modèle d’objet identiques avec des points d’entrée par thread (un modèle de cloisonnement) à utiliser.  
  
 Cette méthode est utilisée pour les hôtes de serveur multithread qui peuvent exécuter plusieurs instances du même script. Le moteur de script peut retourner `E_NOTIMPL`, auquel cas l’hôte peut obtenir le même résultat en dupliquant l’état permanent et en créant une nouvelle instance du moteur de script avec un `IPersist*` interface.  
  
 Cette méthode peut être appelée à partir de threads de l’autre base sans résultant dans une légende de l’autre base d’héberger des objets ou à la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)