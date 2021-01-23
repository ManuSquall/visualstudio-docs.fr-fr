---
title: PROFILE_CURRENTID | Microsoft Docs
description: Découvrez comment utiliser la PROFILE_CURRENTID pour faire fonctionner la fonction sur le thread ou le processus en cours, plutôt que sur un processus spécifiquement indiqué.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5171753ff8ea6722cf1d97e155352e3899fb5562
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719485"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID retourne le pseudo-jeton pour l’ID de thread ou l’ID de processus, dans un appel aux fonctions NameProfile, StartProfile, StopProfile, SuspendProfile et ResumeProfile. Utilisez-le pour que la fonction soit appliquée au thread ou au processus actif, au lieu d’un thread ou processus spécifiquement indiqué.

## <a name="example-1"></a>Exemple 1
 PROFILE_CURRENTID est défini dans *VSPerf.h* comme ceci :

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example-2"></a>Exemple 2
 L’exemple suivant illustre PROFILE_CURRENTID. L’exemple utilise PROFILE_CURRENTID comme paramètre qui identifie le thread actif dans un appel à la fonction [StartProfile](../profiling/startprofile.md).

```cpp
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
- [Informations de référence sur l’API du profileur Visual Studio (natif)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
