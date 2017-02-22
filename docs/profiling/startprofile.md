---
title: "StartProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fonction `StartProfile` affecte au compteur la valeur 1 \(activé\) pour le niveau de profilage spécifié.  
  
## Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### Paramètres  
 `Level`  
  
 Indique le niveau de profil auquel la collection de données de performance peut être appliquée.  Les énumérateurs **PROFILE\_CONTROL\_LEVEL** suivants permettent d'indiquer l'un des trois niveaux auxquels la collection des données de performance peut être appliquée :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|Le paramètre de niveau global affecte tous les processus et threads dans l'exécution du profilage.|  
|PROFILE\_PROCESSLEVEL|Le paramètre au niveau du processus affecte tous les threads qui font partie du processus spécifié.|  
|PROFILE\_THREADLEVEL|Le paramètre au niveau du profilage du thread affecte le thread spécifié.|  
  
 `dwId`  
  
 Identificateur de processus ou de thread généré par le système.  
  
## Valeur de propriété\/valeur de retour  
 La fonction indique la réussite ou l'échec en utilisant l'énumération **PROFILE\_COMMAND\_STATUS**.  La valeur de retour peut être l'une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|L'ID de l'élément de profilage n'existe pas.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|Le niveau de profilage spécifié n'existe pas.|  
|PROFILE\_ERROR\_MODE\_NEVER|La valeur NEVER a été affectée au mode de profilage lors de l'appel à la fonction.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|L'appel de la fonction de profilage, le niveau de profilage ou une combinaison de l'appel et du niveau n'est pas encore implémenté.|  
|PROFILE\_OK|L'appel a réussi.|  
  
## Notes  
 StartProfile et contrôle StopProfile contrôle l'état Start\/Stop du niveau de profilage.  La valeur par défaut de Start\/Stop est 1.  La valeur initiale peut être modifiée dans le Registre.  Chaque appel à StartProfile affecte à Start\/Stop la valeur 1 ; chaque appel à StopProfile lui affecte la valeur 0.  
  
 Lorsque Start\/Stop est supérieur à 0, l'état Start\/Stop de ce niveau est ON.  Lorsqu'il est inférieur ou égal à 0, l'état Start\/Stop est OFF.  
  
 Lorsque l'état Start\/Stop et l'état Suspend\/Resume sont tous deux ON, l'état de profilage du niveau est ON.  Pour qu'un thread soit profilé, les états au niveau global, du processus et du thread doivent être ON.  
  
## Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informations sur la fonction  
 En\-tête : déclaré dans VSPerf.h  
  
 Importez la bibliothèque : VSPerf.lib  
  
## Exemple  
 L'exemple suivant illustre l'appel de la fonction StartProfile.  
  
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
  
## Voir aussi  
 [Référence des API du profileur Visual Studio \(Native\)](../profiling/visual-studio-profiler-api-reference-native.md)