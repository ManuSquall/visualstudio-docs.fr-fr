---
title: PROFILE_CURRENTID | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42ac8c5d7c00be51b3accc662fb0ffb52b5bfab3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54800314"
---
# <a name="profilecurrentid"></a>PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PROFILE_CURRENTID retourne le pseudo-jeton pour l’ID de thread ou l’ID de processus, dans un appel aux fonctions NameProfile, StartProfile, StopProfile, SuspendProfile et ResumeProfile. Utilisez-le pour que la fonction soit appliquée au thread ou au processus actif, au lieu d’un thread ou processus spécifiquement indiqué.  
  
## <a name="example"></a>Exemple  
 PROFILE_CURRENTID est défini dans VSPerf.h comme ceci :  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre PROFILE_CURRENTID. L’exemple utilise PROFILE_CURRENTID comme paramètre qui identifie le thread actif dans un appel à la fonction [StartProfile](../profiling/startprofile.md).  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API du profileur Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)
