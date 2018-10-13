---
title: Utilisation d’exécution des vérifications sans la bibliothèque Runtime C | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02d5128a3d80b7fabe3fd8cf774d5891a66fc20c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263059"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilisation des vérifications à l'exécution sans la bibliothèque Runtime C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous liez votre programme sans la bibliothèque Runtime C, à l’aide **/NODEFAULTLIB**et souhaitez utiliser les contrôles d’exécution, vous devez établir une liaison avec RunTmChk.lib.  
  
 `_RTC_Initialize` initialise le contrôle à l'exécution sur votre programme. Si vous n'établissez pas de liaison avec la bibliothèque Runtime C, avant d'appeler `_RTC_Initialize`, vérifiez que la compilation du programme a prévu la vérification des erreurs au moment de l'exécution :  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Si vous n'établissez pas de liaison avec la bibliothèque Runtime C, vous devez également définir une fonction appelée `_CRT_RTC_INITW`. `_CRT_RTC_INITW` installe votre fonction définie par l'utilisateur comme fonction de rapport d'erreurs par défaut, comme suit :  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Après avoir installé la fonction qui sera utilisée par défaut pour créer le rapport d'erreurs, vous pouvez en installer d'autres avec `_RTC_SetErrorFuncW`. Pour plus d’informations, consultez [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser les vérifications natives à l’exécution](../debugger/how-to-use-native-run-time-checks.md)





