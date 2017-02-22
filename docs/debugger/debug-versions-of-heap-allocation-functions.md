---
title: "Versions Debug des fonctions d&#39;allocation du tas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC (macro)"
  - "_malloc_dbg (fonction)"
  - "déboguer (CRT), fonctions d'allocation du tas"
  - "déboguer les fuites de mémoire, fonctions de la bibliothèque de débogage CRT"
  - "allocation des tas, déboguer"
  - "malloc (fonction)"
  - "fuites de mémoire, fonctions de la bibliothèque de débogage CRT"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Versions Debug des fonctions d&#39;allocation du tas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La bibliothèque Runtime C contient des versions Debug spéciales des fonctions d'allocation du tas.  Ces fonctions utilisent les noms des versions Release, suivis de \_dbg.  Cette rubrique décrit les différences entre la version Release d'une fonction CRT et la version \_dbg à partir d'exemples basés sur `malloc` et `_malloc_dbg`.  
  
 Lorsque [\_DEBUG](/visual-cpp/c-runtime-library/debug) est défini, le CRT mappe tous les appels [malloc](/visual-cpp/c-runtime-library/reference/malloc) sur [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  Il est donc inutile de réécrire votre code en utilisant `_malloc_dbg` à la place de `malloc` pour bénéficier de ses avantages pendant le débogage.  
  
 Vous pouvez cependant appeler `_malloc_dbg` de façon explicite.  Un appel explicite à `_malloc_dbg` présente en outre les avantages suivants :  
  
-   suivi des allocations de type `_CLIENT_BLOCK` ;  
  
-   stockage du fichier source et du numéro de la ligne où la demande d'allocation a été effectuée.  
  
 Si vous ne voulez pas convertir vos appels `malloc` à `_malloc_dbg`, vous pouvez obtenir les informations du fichier source en définissant [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) ; le préprocesseur mappera alors tous les appels à `malloc` directement sur `_malloc_dbg` au lieu d'utiliser un wrapper autour de `malloc`.  
  
 Pour effectuer le suivi des différents types d'allocations dans les blocs client, vous devez appeler `_malloc_dbg` directement et affecter au paramètre `blockType` la valeur `_CLIENT_BLOCK`.  
  
 Lorsque \_DEBUG n'est pas défini, les appels à `malloc` ne sont pas perturbés, les appels à `_malloc_dbg` sont résolus en `malloc`, la définition de [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) est ignorée et les informations des fichiers sources qui se rapportent à la demande d'allocation ne sont pas fournies.  Dans la mesure où `malloc` ne possède aucun paramètre de type de bloc, les demandes de types `_CLIENT_BLOCK` sont traitées comme des allocations standard.  
  
## Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)