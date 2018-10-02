---
title: StartProfile | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8755dcf0b392d17234a3f1224a04de4603840fc2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495639"
---
# <a name="startprofile"></a>StartProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [StartProfile](https://docs.microsoft.com/visualstudio/profiling/startprofile).  
  
La fonction `StartProfile` définit le compteur sur 1 (désactivé) pour le niveau de profilage spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Level`  
  
 Indique le niveau du profil auquel la collecte des données de performances peut être appliquée. Les énumérateurs **PROFILE_CONTROL_LEVEL** suivants peuvent être utilisés pour indiquer un des trois niveaux auxquels la collecte des données de performances peut être appliquée :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Le niveau « global »affecte tous les processus et tous les threads dans l’exécution du profilage.|  
|PROFILE_PROCESSLEVEL|Le niveau « processus » affecte tous les threads qui font partie du processus spécifié.|  
|PROFILE_THREADLEVEL|Le niveau de profilage « thread » affecte le thread spécifié.|  
  
 `dwId`  
  
 Identificateur du processus ou du thread généré par le système.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 La fonction indique la réussite ou l’échec en utilisant l’énumération **PROFILE_COMMAND_STATUS**. La valeur de retour peut être une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|L’ID d’élément de profilage n’existe pas.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Le niveau de profilage spécifié n’existe pas.|  
|PROFILE_ERROR_MODE_NEVER|Le mode de profilage a été défini sur NEVER quand la fonction a été appelée.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|L’appel de fonction du profilage, le niveau de profilage ou la combinaison d’appel et de niveau n’est pas encore implémenté.|  
|PROFILE_OK|L’appel a réussi.|  
  
## <a name="remarks"></a>Notes  
 StartProfile et StopProfile contrôlent l’état Start/Stop pour le niveau de profilage. La valeur par défaut de Start/Stop est 1. La valeur initiale peut être changée dans le Registre. Chaque appel à StartProfile définit Start/Stop sur 1 ; chaque appel à StopProfile le définit sur 0.  
  
 Quand Start/Stop est supérieur à 0, l’état de Start/Stop pour le niveau est ON. Quand il est inférieur ou égal à 0, l’état de Start/Stop est OFF.  
  
 Quand l’état Start/Stop et l’état Suspend/Resume sont tous deux ON, l’état du profilage pour le niveau est ON. Pour qu’un thread soit profilé, les états des niveaux Global, Processus et Thread pour le thread doivent tous être ON.  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informations sur la fonction  
 En-tête : déclaré dans VSPerf.h  
  
 Bibliothèque d’importation : VSPerf.lib  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’appel de la fonction StartProfile.  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
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



