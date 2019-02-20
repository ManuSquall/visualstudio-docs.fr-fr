---
title: 'Comment : définir un nom de Thread en Code natif | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c547dd00f7a5a31b949d22c13f305050355207c7
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227314"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Comment : définir un nom de thread dans le code natif
Il est possible d'attribuer des noms aux threads dans toutes les éditions de Visual Studio. Ces noms sont utiles pour identifier les threads d’intérêt dans le **Threads** fenêtre lors du débogage d’un processus en cours d’exécution. Avoir nommé évidente de threads peut également être utile lors de l’exécution via l’inspection de vidage sur incident et de l’analyse des performances de capture à l’aide de divers outils de débogage post-mortem.

## <a name="ways-to-set-a-thread-name"></a>Méthodes pour définir un nom de thread

Il existe deux façons de définir un nom de thread. La première consiste à utiliser le [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) (fonction). La deuxième consiste à lever une exception particulière que le débogueur Visual Studio est attaché au processus. Chaque approche présente des avantages et inconvénients.

Il est important de souligner que _à la fois_ approches peuvent être utilisés ensemble, si vous le souhaitez, dans la mesure où les mécanismes par lesquels ils travaillent sont indépendants des uns des autres.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Définir un nom de thread à l’aide de `SetThreadDescription`

Avantages :
* Noms de thread sont visibles lors du débogage dans Visual Studio, quel que soit ou non le débogueur a été attaché au processus au moment où SetThreadDescription est appelée.
* Noms de thread sont visibles lorsque vous effectuez le débogage post-mortem en chargeant un vidage sur incident dans Visual Studio.
* Noms de thread sont également visibles lors de l’utilisation d’autres outils, tels que le [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) débogueur et le [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) Analyseur de performances.

Avertissements :
* Noms de thread sont uniquement visibles dans Visual Studio 2017 version 15.6 et versions ultérieures.
* Lorsque le fichier de vidage du débogage d’un incident post-mortem, les noms de thread sont visibles uniquement si l’incident a été créé sur Windows 10 version 1607, Windows Server 2016 ou versions ultérieures de Windows.

*Exemple :*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Définir un nom de thread en levant une exception

Un autre pour définir un nom de thread dans votre programme consiste à communiquer le nom de thread souhaité pour le débogueur Visual Studio en levant une exception spécialement configuré.

Avantages :
* Fonctionne dans toutes les versions de Visual Studio.

Avertissements :
* Fonctionne uniquement si le débogueur est attaché au moment de que l’utilisation de la méthode basée sur l’exception.
* Les noms de thread définies à l’aide de cette méthode ne sera pas disponibles dans les dumps ou des outils d’analyse de performances.

*Exemple :*

Le `SetThreadName` fonction ci-dessous illustre cette approche basée sur l’exception. Notez que le nom de thread est copié automatiquement vers le thread, afin que la mémoire pour le `threadName` paramètre peut être libéré après le `SetThreadName` appel est terminé.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>Voir aussi
[Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)  
[Guide pratique pour définir un nom de thread dans le code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)
