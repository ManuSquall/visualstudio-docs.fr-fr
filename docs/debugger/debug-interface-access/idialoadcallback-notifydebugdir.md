---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyDebugDir (méthode)"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Appelé lorsqu'un répertoire de débogage a été trouvé dans le fichier .exe.  
  
## Syntaxe  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### Paramètres  
 `fExecutable`  
 \[in\]  `TRUE` si le répertoire debug est lu à partir d'un fichier exécutable \(plutôt qu'un fichier de .dbg\).  
  
 `cbData`  
 \[in\]  nombre d'octets de données dans le répertoire de débogage.  
  
 `data[]`  
 \[in\]  Un tableau qui est effectuée avec un répertoire de débogage.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le code de retour est généralement abandonné.  
  
## Notes  
 La méthode d' [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) appelle ce rappel lorsqu'il recherche un répertoire de débogage pendant le traitement de l'exécutable.  
  
 Cette méthode supprime le besoin de client pour des le fichier exécutable et\/ou le fichier de débogage pour prendre en charge des informations de débogage autre que celui trouvé dans le fichier .pdb.  Avec ces données, le client peut identifier le type d'informations de débogage disponible et s'il réside dans le fichier exécutable ou le fichier de .dbg.  
  
 La plupart des clients n'auront pas besoin de ce rappel car la méthode d' `IDiaDataSource::loadDataForExe` ouvre de façon transparente .pdb et de fichiers .dbg si nécessaire pour servir les symboles.  
  
## Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)