---
title: "Fonctions de raccordement de rapport | Microsoft Docs"
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
  - "_CrtDbgReport (fonction)"
  - "_CrtSetReportHook (fonction)"
  - "débogueur, fonctions de raccordement de rapport"
  - "déboguer (C++), fonctions de raccordement"
  - "raccordements, rapport"
  - "allocation de mémoire, tas de débogage"
  - "fonctions de raccordement de rapport"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Fonctions de raccordement de rapport
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une fonction de raccordement de rapport, installée avec [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook), est appelée chaque fois que [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) génère un rapport de débogage.  Vous pouvez vous en servir, entre autres, pour filtrer les rapports de façon à vous concentrer sur des types d'allocations spécifiques.  Une fonction de raccordement de rapport doit avoir un prototype similaire au suivant :  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Le pointeur que vous passez à **\_CrtSetReportHook** est du type **\_CRT\_REPORT\_HOOK**, comme cela est défini dans CRTDBG.H :  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre fonction de raccordement, l'argument *nRptType* contient la catégorie du rapport \(**\_CRT\_WARN**, **\_CRT\_ERROR** ou **\_CRT\_ASSERT**\), *szMsg* contient un pointeur vers une chaîne de message de rapport entièrement assemblé et *retVal* spécifie si `_CrtDbgReport` doit poursuivre normalement son exécution après avoir généré le rapport ou démarrer le débogueur. \(Si la valeur de *retVal* est zéro, l'exécution se poursuit, si cette valeur est 1, le débogueur est démarré.\)  
  
 Si le raccordement gère intégralement le message concerné et qu'aucun rapport supplémentaire n'est requis, il devrait retourner la valeur **TRUE**.  S'il retourne **FALSE**, `_CrtDbgReport` communiquera le message de la façon normale.  
  
## Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/fr-fr/21e1346a-6a17-4f57-b275-c76813089167)