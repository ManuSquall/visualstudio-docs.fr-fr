---
title: "IDiaEnumSectionContribs::Item | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Item (méthode)"
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les contributions de section à l'aide d'un index.  
  
## Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### Paramètres  
 index  
 \[in\]  Index de l'objet d' [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) à récupérer.  L'index est comprise entre 0 et `count`\-1, où `count` est retourné par la méthode d' [IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md) .  
  
 section  
 \[out\]  Retourne un objet d' [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) représentant la contribution spécifique de section.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)