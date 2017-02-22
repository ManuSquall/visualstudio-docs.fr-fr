---
title: "Comment&#160;: d&#233;finir un nom de thread dans le code natif | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer (C++), threads"
  - "déboguer (Visual Studio), threads"
  - "SetThreadName (fonction)"
  - "noms de threads"
  - "threads (Visual Studio), noms"
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# Comment&#160;: d&#233;finir un nom de thread dans le code natif
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour définir le nom d'un thread dans votre programme, utilisez la fonction `SetThreadName`, comme le montre l'exemple de code suivant. Notez que le nom de thread est copié vers le thread de sorte que la mémoire du paramètre `threadName` puisse être libérée.  
  
## Exemple  
  
```cpp  
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
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Comment : définir un nom de thread dans le code managé](../debugger/how-to-set-a-thread-name-in-managed-code.md)