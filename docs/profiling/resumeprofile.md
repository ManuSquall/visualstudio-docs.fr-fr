---
title: ResumeProfile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb0f988ce0d1b266fd930909f6e5d6462929e8f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="resumeprofile"></a>ResumeProfile
La méthode `ResumeProfile` décrémente le compteur Suspend/Resume pour le niveau de profilage spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
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
  
## <a name="remarks"></a>Remarques  
 La valeur initiale du compteur de pauses/reprises est 0. Chaque appel à SuspendProfile ajoute 1 au nombre de Suspend/Resume ; chaque appel à ResumeProfile soustrait 1.  
  
 Quand le nombre de Suspend/Resume est supérieur à 0, l’état Suspend/Resume pour le niveau est ON. Quand le nombre est inférieur ou égal à 0, l’état Suspend/Resume est ON.  
  
 Quand l’état Start/Stop et l’état Suspend/Resume sont tous deux ON, l’état du profilage pour le niveau est ON. Pour qu’un thread soit profilé, les états des niveaux Global, Processus et Thread pour le thread doivent tous être ON.  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informations sur la fonction  
 En-tête : déclaré dans VSPerf.h  
  
 Bibliothèque d’importation : VSPerf.lib  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la fonction ResumeProfile. L’exemple suppose qu’un appel à la méthode SuspendProfile a été effectué pour le même thread ou processus identifié par [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API du profileur Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)