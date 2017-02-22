---
title: "IDiaSectionContrib::get_dataCrc | Microsoft Docs"
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
  - "IDiaSectionContrib::get_dataCrc (méthode)"
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSectionContrib::get_dataCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère le contrôle de \(CRC\) redondance cyclique des données dans la section.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_dataCrc (   
   DWORD* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne CRC des données dans la section.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)