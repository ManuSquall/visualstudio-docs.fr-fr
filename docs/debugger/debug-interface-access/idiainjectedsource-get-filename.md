---
title: "IDiaInjectedSource::get_filename | Microsoft Docs"
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
  - "IDiaInjectedSource::get_filename (méthode)"
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_filename
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait le nom de fichier de la source.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### Paramètres  
 pRetVal  
 \[out\]  Retourne le nom de fichier de la source.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)