---
title: Fonctions de raccordement de rapport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 97d39a171d812915a1cf3c1c6450c73098067949
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284196"
---
# <a name="report-hook-functions"></a>Fonctions de raccordement de rapport
Une fonction de raccordement de rapport, installée à l’aide [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), est appelée chaque fois [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) génère un rapport de débogage. Vous pouvez vous en servir, entre autres, pour filtrer les rapports de façon à vous concentrer sur des types d'allocations spécifiques. Une fonction de raccordement de rapport doit avoir un prototype similaire au suivant :  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Le pointeur que vous passez à **_CrtSetReportHook** est de type **_CRT_REPORT_HOOK**, tel que défini dans CRTDBG. H :  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre fonction de raccordement, le *nRptType* argument contient la catégorie du rapport (**_CRT_WARN**, **_CRT_ERROR**, ou **_CRT _ASSERT**), *szMsg* contient un pointeur vers une chaîne de message de rapport entièrement assemblé et *retVal* Spécifie si `_CrtDbgReport` doivent poursuivre leur exécution normale Après avoir généré le rapport ou démarrez le débogueur. (Un *retVal* valeur zéro continue l’exécution, la valeur 1 démarre le débogueur.)  
  
 Si le raccordement gère intégralement le message concerné et qu’aucun rapport supplémentaire n’est requis, il doit retourner **TRUE**. Si elle retourne **FALSE**, `_CrtDbgReport` communiquera le message normalement.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
