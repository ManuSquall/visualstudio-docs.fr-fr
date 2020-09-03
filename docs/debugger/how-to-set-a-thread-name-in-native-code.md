---
title: Comment définir un nom de thread dans du code natif | Microsoft Docs
ms.date: 12/17/2018
ms.topic: how-to
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
ms.openlocfilehash: ce6281a87900247cc54422a5175714d5f05b8e07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349144"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Comment : définir un nom de thread dans le code natif
Il est possible d'attribuer des noms aux threads dans toutes les éditions de Visual Studio. L’attribution de noms aux threads est utile pour identifier les threads intéressants dans la fenêtre **Threads** lors du débogage d’un processus en cours d’exécution. Le fait de disposer de threads de nom reconnaissables peut également être utile pour effectuer un débogage après un vidage sur incident et lors de l’analyse des captures de performances à l’aide de différents outils.

## <a name="ways-to-set-a-thread-name"></a>Comment définir un nom de thread

Il existe deux façons de définir un nom de thread. La première consiste à utiliser la fonction [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . La seconde consiste à lever une exception particulière alors que le débogueur Visual Studio est attaché au processus. Chaque approche présente des avantages et des inconvénients. L’utilisation de `SetThreadDescription` est prise en charge à partir de Windows 10, version 1607 ou Windows Server 2016.

Il est à noter que _les deux_ approches peuvent être utilisées ensemble, si vous le souhaitez, étant donné que les mécanismes par lesquels elles fonctionnent sont indépendants les uns des autres.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Définir un nom de thread à l’aide de `SetThreadDescription`

Avantages :
* Les noms de threads sont visibles lors du débogage dans Visual Studio, que le débogueur ait ou non été attaché au processus au moment de l’appel de SetThreadDescription.
* Les noms de threads sont visibles lors de l’exécution d’un débogage après le chargement d’un vidage sur incident dans Visual Studio.
* Les noms de thread sont également visibles lors de l’utilisation d’autres outils, tels que le débogueur [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) et l’analyseur de performances [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) .

Avertissements :
* Les noms de threads sont visibles uniquement dans Visual Studio 2017 version 15,6 et versions ultérieures.
* Lors du débogage d’un fichier de vidage sur incident, les noms de threads sont visibles uniquement si l’incident a été créé sur Windows 10 version 1607, Windows Server 2016 ou versions ultérieures de Windows.

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

Une autre façon de définir un nom de thread dans votre programme consiste à communiquer le nom de thread souhaité au débogueur Visual Studio en levant une exception spécialement configurée.

Avantages :
* Fonctionne dans toutes les versions de Visual Studio.

Avertissements :
* Fonctionne uniquement si le débogueur est attaché au moment où la méthode basée sur une exception est utilisée.
* Les noms de thread définis à l’aide de cette méthode ne seront pas disponibles dans les outils de vidage ou d’analyse des performances.

*Exemple :*

La `SetThreadName` fonction illustrée ci-dessous illustre cette approche basée sur une exception. Notez que le nom du thread sera automatiquement copié dans le thread, afin que la mémoire du `threadName` paramètre puisse être libérée une fois l' `SetThreadName` appel terminé.

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
- [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
- [Comment : définir un nom de thread dans le code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)
