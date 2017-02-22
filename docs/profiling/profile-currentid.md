---
title: "PROFILE_CURRENTID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PROFILE_CURRENTID"
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

PROFILE\_CURRENTID retourne le pseudo\-jeton de l'ID du thread ou du processus, dans un appel aux fonctions NameProfile, StartProfile, StopProfile, SuspendProfile et ResumeProfile.  Utilisez cette propriété pour forcer la fonction à opérer sur le thread ou le processus actuel, plutôt que sur un thread ou processus spécifiquement indiqué.  
  
## Exemple  
 PROFILE\_CURRENTID est défini dans VSPerf.h comme :  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## Exemple  
 L'exemple suivant illustre PROFILE\_CURRENTID.  L'exemple utilise PROFILE\_CURRENTID comme un paramètre qui identifie le thread actuel dans un appel à la fonction [StartProfile](../profiling/startprofile.md).  
  
```  
void ExerciseProfileCurrentID()  
{  
    // Declare ProfileOperationResult enumeration   
    // to hold return value of a call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    profileResult = StartProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Voir aussi  
 [Référence des API du profileur Visual Studio \(Native\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)