---
title: "IDiaSectionContrib::get_relocationsCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_relocationsCrc (méthode)"
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSectionContrib::get_relocationsCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le contrôle de \(CRC\) redondance cyclique des informations de réadressage de la section.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_relocationsCrc (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne CRC des informations de réadressage de la section.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)