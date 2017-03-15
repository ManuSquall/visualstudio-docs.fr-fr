---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt (méthode)"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lit le nombre d'octets spécifié en commençant à l'offset spécifié à partir d'un fichier exécutable.  
  
## Syntaxe  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Paramètres  
 fileOffset  
 \[in\]  L'offset dans le fichier exécutable à démarrer la lecture.  
  
 cbData  
 \[in\]  Nombre d'octets à lire.  
  
 pcbData  
 \[out\]  Retourne le nombre d'octets.  
  
 données \[\]  
 \[in, out\]  Un tableau qui est terminée avec des octets indique à partir de le fichier.  
  
## Notes  
 Cette méthode est appelée par le code de prise en charge de diamètre pour charger des octets de données d'un fichier exécutable à l'aide d'un offset de fichier absolu.  cette méthode est appelée à l'appui de la méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## Voir aussi  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)