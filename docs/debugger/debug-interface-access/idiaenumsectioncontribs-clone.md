---
title: "IDiaEnumSectionContribs::Clone | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Clone (méthode)"
ms.assetid: 81d3f3a7-3684-4e5c-b028-29b268684a2c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSectionContribs::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.  
  
## Syntaxe  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumSectionContrib** ppenum  
);  
```  
  
#### Paramètres  
 ppenum  
 \[out\]  Retourne un objet d' [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) qui contient un doublon de l'énumérateur.  Les contributions de section ne sont pas dupliquées, seul l'énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)