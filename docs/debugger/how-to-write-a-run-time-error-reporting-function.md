---
title: Écrire une fonction de création de rapports d’erreurs au moment de l’exécution | Microsoft Docs
description: Consultez des exemples d’écriture d’une fonction personnalisée de création de rapports d’erreurs au moment de l’exécution dans Visual Studio. Elle doit avoir la même déclaration que _CrtDbgReportW et retourner la valeur 1.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ff82afdfda8af746533f07f21d330c359a1618c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385135"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Guide pratique pour écrire une fonction de création de rapports d’erreurs d’exécution (C++)
Si vous créez une fonction personnalisée destinée à rapporter les erreurs d'exécution, elle doit avoir la même déclaration que `_CrtDbgReportW`. Elle doit retourner au débogueur une valeur égale à 1.

L'exemple suivant montre comment définir cette fonction personnalisée.

## <a name="example-1"></a>Exemple 1

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example-2"></a>Exemple 2
La fonction personnalisée de l'exemple suivant est un peu plus complexe. Dans cet exemple, l'instruction switch gère divers types d'erreurs, tels qu'ils sont définis dans le paramètre `reportType` de `_CrtDbgReportW`. Étant donné que vous remplacez `_CrtDbgReportW`, vous ne pouvez pas utiliser `_CrtSetReportMode`. Votre fonction doit gérer la sortie. Le premier argument variable de cette fonction prend un numéro d’erreur d’exécution. Pour plus d’informations, consultez [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example-3"></a>Exemple 3
Utilisez `_RTC_SetErrorFuncW` pour installer votre fonction personnalisée à la place de `_CrtDbgReportW`. Pour plus d’informations, consultez [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). La valeur de retour de `_RTC_SetErrorFuncW` est la fonction de rapport précédente, que vous pouvez enregistrer et restaurer si nécessaire.

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>Voir aussi
[Personnalisation des contrôles de Run-Time natifs](../debugger/native-run-time-checks-customization.md)
