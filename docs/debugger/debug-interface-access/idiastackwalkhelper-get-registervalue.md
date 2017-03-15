---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::get_registerValue (méthode)"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

extrait la valeur d'un registre.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Paramètres  
 `index`  
 \[in\]  une valeur de spécifier d'énumération de [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) dont enregistrez\-vous pour obtenir la valeur.  
  
 `pRetVal`  
 \[out\]  Retourne la valeur actuelle du registre.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 En dépit de la taille du paramètre d' `pRetVal` , une implémentation doit stocker uniquement ce que le registre contient normalement.  Par exemple, un registre de 8 bits contient uniquement les plus bas 8 bits de la valeur donnée.  Cette valeur 8 bits est développée à 64 bits une fois retournée par cette méthode.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)