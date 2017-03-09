---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit par sa présence si le fichier journal de graphiques est enregistré au répertoire des fichiers temporaires de l'utilisateur.  
  
## Syntaxe  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## Valeur  
 Un symbole de préprocesseur détermine par sa présence ou son absence si le fichier journal de graphiques est enregistré au répertoire des fichiers temporaires de l'utilisateur.  Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire actif de l'application capturée, ou un chemin d'accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire des fichiers temporaires de l'utilisateur et ne peut pas être un chemin d'accès absolu.  
  
## Remarques  
 Selon les privilèges de l'utilisateur, le fichier journal graphiques peut ne pas pouvoir être stocké dans un emplacement aléatoire.  Il est préférable que vous préférez sauvegarder des journaux de graphiques au répertoire des fichiers temporaires de l'utilisateur, ou un autre bon emplacement, si vous ne savez pas si l'emplacement que vous choisiriez puisse être écrit en l'utilisateur.  
  
 Pour empêcher le fichier journal de graphiques d'être enregistré au répertoire des fichiers temporaires, vous devez `DONT_SAVE_VSGLOG_TO_TEMP` défini avant d'inclure `vsgcapture.h`.  
  
## Exemple  
 Cet exemple montre comment enregistrer le fichier journal de graphiques à un chemin d'accès absolu sur l'ordinateur \- hôte.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## Voir aussi  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)