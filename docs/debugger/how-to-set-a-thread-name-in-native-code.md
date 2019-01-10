---
title: 'Procédure : Définir un nom de Thread en Code natif | Microsoft Docs'
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: acddd39df0c91aeef5c425ffa67cb234d76d0473
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961346"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Procédure : définir un nom de thread dans du code natif
Il est possible d'attribuer des noms aux threads dans toutes les éditions de Visual Studio. Ces noms sont utiles pour effectuer le suivi des threads dans la fenêtre **Threads**.

## <a name="set-a-thread-name"></a>Définir un nom de thread

Le `SetThreadName` fonction est utile pour la définition et la consultation des threads si le débogueur est attaché à votre code en cours d’exécution. À partir de Visual Studio 2017 version 15.6, vous pouvez utiliser la [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) fonction pour définir et afficher les noms de thread.

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

## <a name="set-a-thread-name-using-setthreadname"></a>Définir un nom de thread à l’aide de SetThreadName

Pour définir un nom de thread dans votre programme, vous pouvez également utiliser le `SetThreadName` de fonction, comme indiqué dans l’exemple de code suivant. Notez que le nom de thread est copié vers le thread de sorte que la mémoire du paramètre `threadName` puisse être libérée.  Cette méthode utilise une approche basée sur les exceptions qui ne fonctionne que si le débogueur est attaché au moment de que l’utilisation de la méthode basée sur l’exception. Un nom de thread que vous définissez à l’aide de cette méthode ne sera pas disponible dans les dumps ou des outils d’analyse de performances.

L’exemple de code suivant montre comment utiliser `SetThreadName`:

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
 [Guide pratique pour définir un nom de thread dans du code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)