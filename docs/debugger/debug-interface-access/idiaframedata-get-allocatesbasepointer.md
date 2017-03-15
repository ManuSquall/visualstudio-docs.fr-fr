---
title: "IDiaFrameData::get_allocatesBasePointer | Microsoft Docs"
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
  - "IDiaFrameData::get_allocatesBasePointer (méthode)"
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait une balise qui indique si le pointeur de base est alloué pour le code dans cette plage d'adresses.  Cette méthode est déconseillée.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne `TRUE` si un pointeur de base est alloué ; sinon, retourne `FALSE`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Cette propriété doit être utilisée uniquement par le code qui était auparavant accédé à FPO\_DATA, ou lorsque la chaîne de programme retournée par la méthode d' [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) est `NULL`.  Sinon, la chaîne de programme contient toutes les informations nécessaires pour calculer des valeurs précédentes de registre.  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)