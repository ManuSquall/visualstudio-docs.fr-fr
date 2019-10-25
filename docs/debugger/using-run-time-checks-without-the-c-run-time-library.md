---
title: Utilisation de contrôles d’exécution sans la bibliothèque Runtime C | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 029aafa634ba0e6837cdc7d4304d0419420dd912
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728664"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilisation des vérifications à l'exécution sans la bibliothèque Runtime C
Si vous liez votre programme sans la bibliothèque Runtime C, en utilisant **/NODEFAULTLIB**et que vous souhaitez utiliser des contrôles à l’exécution, vous devez effectuer une liaison avec RunTmChk. lib.

`_RTC_Initialize` initialise le contrôle à l'exécution sur votre programme. Si vous n'établissez pas de liaison avec la bibliothèque Runtime C, avant d'appeler `_RTC_Initialize`, vérifiez que la compilation du programme a prévu la vérification des erreurs au moment de l'exécution :

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Si vous n'établissez pas de liaison avec la bibliothèque Runtime C, vous devez également définir une fonction appelée `_CRT_RTC_INITW`. `_CRT_RTC_INITW` installe votre fonction définie par l'utilisateur comme fonction de rapport d'erreurs par défaut, comme suit :

```cpp
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

Après avoir installé la fonction qui sera utilisée par défaut pour créer le rapport d'erreurs, vous pouvez en installer d'autres avec `_RTC_SetErrorFuncW`. Pour plus d’informations, consultez [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Voir aussi
[Guide pratique pour utiliser les vérifications natives à l’exécution](../debugger/how-to-use-native-run-time-checks.md)
