---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::put_registerValue (méthode)"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

définit la valeur d'un registre.  
  
## Syntaxe  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Paramètres  
 `index`  
 \[in\]  Une valeur de l'énumération de [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) spécifiant le registre pour écrire.  
  
 `NewVal`  
 \[in\]  la nouvelle valeur de registre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 En dépit de la taille de la valeur, une implémentation doit stocker uniquement ce que le registre contient normalement.  Par exemple, un registre de 8 bits maintiendrait uniquement les plus bas 8 bits de la valeur donnée.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)