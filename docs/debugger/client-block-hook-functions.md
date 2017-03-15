---
title: "Fonctions de raccordement de bloc client | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtSetDumpClient (fonction)"
  - "blocs clients, fonctions de raccordement"
  - "blocs clients, valider des données et édition d'un rapport de données"
  - "déboguer (C++), fonctions de raccordement"
  - "raccordements, bloc client"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Fonctions de raccordement de bloc client
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous voulez valider ou reporter le contenu des données stockées dans des blocs `_CLIENT_BLOCK`, vous pouvez écrire une fonction spécialement dans ce but.  Cette fonction doit avoir un prototype similaire au suivant, défini dans CRTDBG.H :  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En d'autres termes, votre fonction de raccordement doit accepter un pointeur **void** vers le début du bloc d'allocation, avec une valeur de type **size\_t** indiquant la taille de l'allocation, et retourner `void`.  Pour le reste, son contenu dépend de vous.  
  
 Une fois que vous avez installé votre fonction de raccordement avec [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient), elle est appelée à chaque dump d'un bloc `_CLIENT_BLOCK`.  Vous pouvez alors utiliser [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) pour obtenir des informations sur le type ou le sous\-type des blocs ayant fait l'objet d'un dump.  
  
 Le pointeur vers votre fonction passé à `_CrtSetDumpClient` est du type **\_CRT\_DUMP\_CLIENT**, comme défini dans CRTDBG.H :  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/fr-fr/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)