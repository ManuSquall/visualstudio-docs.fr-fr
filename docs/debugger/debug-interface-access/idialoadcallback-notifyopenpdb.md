---
title: "IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyOpenPDB (méthode)"
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyOpenPDB
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Appelé lorsqu'un fichier de candidat .pdb est ouvert.  
  
## Syntaxe  
  
```cpp#  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### Paramètres  
 `pdbPath`  
 \[in\]  Le chemin d'accès complet du fichier .pdb.  
  
 `resultCode`  
 \[in\]  Le code qui indique succès \(`S_OK`\) ou l'échec de la charge comme appliqué ce fichier.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le code de retour est généralement abandonné.  
  
## Voir aussi  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)