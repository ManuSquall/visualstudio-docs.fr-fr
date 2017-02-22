---
title: "IDiaEnumSourceFiles::Item | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Item (méthode)"
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSourceFiles::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait un fichier source au moyen d'un index.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'objet d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) à récupérer.  L'index est comprise entre 0 et `count`\-1, où`count` est retourné par la méthode d' [IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md) .  
  
 sourceFile  
 \[out\]  Retourne un objet d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) représentant le fichier source souhaité.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)