---
title: "IDiaTable::Item | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaTable::Item (méthode)"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait une référence à l'entrée spécifiée dans le tableau.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### Paramètres  
 `index`  
 \[in\]  l'index de l'entrée de table dans la plage 0 à `count`\-1, où `count` est retourné par la méthode d' [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 \[out\]  Retourne un objet d' `IUnknown` qui représente l'entrée de table spécifiée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 un tableau représente une collection d'objets.  Selon ces objets, le paramètre d'élément peut être casté à l'interface appropriée.  Par exemple, si une table contient des objets d' [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , le paramètre de l'élément peut être casté à l'interface d' `IDiaSegment` .  
  
 Il s'agit de l'approche courante pour appeler la méthode d' `QueryInterface` dans l'interface d' [IDiaTable](../../debugger/debug-interface-access/idiatable.md) pour l'interface appropriée d'énumérateur et d'utiliser les méthodes spécifiques de l'énumérateur pour accéder au contenu.  Consultez l'interface d' [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) pour obtenir un exemple.  
  
## Voir aussi  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)