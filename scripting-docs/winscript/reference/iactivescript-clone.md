---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
Clone le moteur de script actuel \(moins un état en cours de exécution\), en retournant un moteur de script chargé sans site dans le thread actuel.  Les propriétés de ce nouveau moteur de script sont identiques aux propriétés que le moteur de script d'origine est dans le cas transitioned vers l'état initialisé.  
  
## Syntaxe  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### Paramètres  
 `ppscript`  
 \[out\]  Adresse d'une variable qui reçoit un pointeur vers l'interface d' [IActiveScript](../../winscript/reference/iactivescript.md) du moteur de script cloné.  L'hôte doit créer un site et appeler la méthode d' [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) sur le nouveau moteur de script avant d'être dans l'état initialisé et, par conséquent, utilisable.  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_NOTIMPL`|Cette méthode n'est pas prise en charge.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
  
## Notes  
 La méthode d' `IActiveScript::Clone` est une optimisation de `IPersist*::Save`, d' `CoCreateInstance`, et d' `IPersist*::Load`, l'état du nouveau moteur de script doit être le même que si l'état du moteur de script d'origine ont été enregistrés et chargés dans un nouveau moteur de script.  Les éléments nommés sont en double dans le moteur de script clonés, mais des pointeurs d'objets spécifiques pour chaque élément sont oubliés et sont obtenus à la méthode d' [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) .  Cela permet un modèle objet identique à des points d'entrée par thread \(un modèle cloisonné\) à utiliser.  
  
 Cette méthode est utilisée pour les hôtes multithread de serveur qui peut exécuter plusieurs instances du même script.  Le moteur de script peut retourner `E_NOTIMPL`dans ce cas, l'hôte peut obtenir le même résultat dupliquant l'état de persistance et en créant une nouvelle instance du moteur de script avec une interface d' `IPersist*` .  
  
 Cette méthode peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à l'interface d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)