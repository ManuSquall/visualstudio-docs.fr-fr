---
title: Fonctions de raccordement de rapport | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84105fa1a3d7bf5c6f949421b306b5147368a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892353"
---
# <a name="report-hook-functions"></a>Fonctions de raccordement de rapport
Une fonction de raccordement de rapport, installée avec [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), est appelée chaque fois que [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) génère un rapport de débogage. Vous pouvez vous en servir, entre autres, pour filtrer les rapports de façon à vous concentrer sur des types d'allocations spécifiques. Une fonction de raccordement de rapport doit avoir un prototype similaire au suivant :  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Le pointeur que vous passez à **_CrtSetReportHook** est de type **_CRT_REPORT_HOOK**, tel que défini dans CRTDBG. H :  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quand la bibliothèque Runtime appelle votre fonction de raccordement, l’argument *nRptType* contient la catégorie du rapport (**_CRT_WARN**, **_CRT_ERROR**, or **_CRT_ASSERT**), *szMsg* contient un pointeur vers une chaîne de message de rapport entièrement assemblé, et *retVal* spécifie si `_CrtDbgReport` doit poursuivre normalement son exécution après avoir généré le rapport ou bien démarrer le débogueur. (Si la valeur de *retVal* est zéro, l’exécution se poursuit ; si cette valeur est 1, le débogueur est démarré.)  
  
 Si le raccordement gère intégralement le message concerné et qu’aucun rapport supplémentaire n’est requis, il devrait retourner la valeur **TRUE**. S’il retourne **FALSE**, `_CrtDbgReport` communique le message de façon normale.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
