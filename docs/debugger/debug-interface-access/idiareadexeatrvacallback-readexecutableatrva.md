---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA (méthode)"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit le nombre d'octets spécifié à partir de l'adresse virtuelle relative spécifiée \(RVA\) du fichier exécutable.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Paramètres  
 `relativeVirtualAddress`  
 \[in\]  Le CONCERNANT dans le fichier exécutable à démarrer la lecture.  
  
 `cbData`  
 \[in\]  Nombre d'octets à lire.  
  
 `pcbData`  
 \[out\]  Retourne le nombre d'octets.  
  
 `data[]`  
 \[in, out\]  Un tableau qui est terminée avec des octets indique à partir de le fichier.  
  
## Notes  
 Cette méthode est appelée par le code de prise en charge de diamètre pour charger des octets de données d'un fichier exécutable utilisant une adresse virtuelle associée.  cette méthode est appelée à l'appui de la méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## Voir aussi  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)