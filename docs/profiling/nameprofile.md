---
title: "NameProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fonction `NameProfile` assigne une chaîne au processus ou au thread spécifié.  
  
 L'API NameProfile est uniquement disponible pour le profilage d'instrumentation.  L'API NameProfile n'est pas prise en charge pour le profilage d'échantillonnage.  
  
## Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### Paramètres  
 `pszName`  
  
 Nom de l'élément de profilage.  Un nom n'est pas valide \(provoquant le retour par NameProfileA de NAME\_ERROR\_INVALID\_NAME\) si :  
  
-   Le pointeur passé dans NameProfileA est une valeur NULL  
  
-   Les données de type chaîne de pszName commencent par un nombre  
  
-   Les données de type chaîne de pszName contiennent un espace  
  
-   Les données de type chaîne de pszName contiennent chacun des caractères suivants : ,;.\`~\!@\#$%^&\*\(\)\=\[\]{}&#124;\\?\/\<\>  
  
 `Level`  
  
 Indique le niveau de profil auquel la collection de données de performance peut être appliquée.  Les valeurs **PROFILE\_CONTROL\_LEVEL** suivantes permettent d'indiquer l'un des trois niveaux auxquels la collection des données de performance peut être appliquée :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|Le paramètre de niveau global affecte tous les processus et threads dans l'exécution du profilage.|  
|PROFILE\_PROCESSLEVEL|Le paramètre au niveau du processus affecte tous les threads qui font partie du processus spécifié.|  
|PROFILE\_THREADLEVEL|Le paramètre au niveau du profilage du thread affecte le thread spécifié.|  
  
 `dwId`  
  
 Identificateur du niveau de profilage.  Utilisez l'identificateur de processus ou de thread généré par le système.  
  
## Valeur de propriété\/valeur de retour  
 La fonction indique la réussite ou l'échec en utilisant l'énumération **PROFILE\_COMMAND\_STATUS**.  La valeur de retour peut être l'une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|NAME\_ERROR\_ID\_NOEXIST|L'élément de profilage spécifié n'existe pas.|  
|NAME\_ERROR\_INVALID\_NAME|Le nom n'est pas valide.|  
|NAME\_ERROR\_LEVEL\_NOEXIST|Le niveau de profil spécifié n'existe pas.|  
|NAME\_ERROR\_NO\_SUPPORT|L'opération spécifiée n'est pas prise en charge.|  
|NAME\_ERROR\_OUTOFMEMORY|La mémoire n'était pas disponible pour enregistrer l'événement.|  
|NAME\_ERROR\_REDEFINITION|Un nom a déjà été assigné à l'élément de profil.  Le nom dans cette fonction est ignoré.|  
|NAME\_ERROR\_TEXTTRUNCATED|Le texte du nom a dépassé 32 caractères y compris le caractère Null et a été donc tronqué.|  
|NAME\_OK|Le nom a été enregistré avec succès.|  
  
## Notes  
 Un seul nom peut être assigné à chaque processus ou thread.  Une fois qu'un élément de profilage est nommé, les appels suivants à NameProfile pour cet élément sont ignorés.  
  
 Si le même nom est attribué à des threads ou processus différents, le rapport inclura les données de tous les éléments à ce niveau avec ce nom.  
  
 Si vous spécifiez un processus ou un thread différent de l'actuel, vous devez vérifier qu'il a été initialisé et qu'il a commencé à s'exécuter avant de le nommer.  Sinon, la méthode NameProfile échoue.  
  
> [!IMPORTANT]
>  Les fonctions d'API CreateProcess\(\) et CreateThread\(\) peuvent être retournées avant que le thread ou le processus ne soit initialisé.  
  
## Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informations sur la fonction  
  
|||  
|-|-|  
|**Header**|Inclure VSPerf.h|  
|**Bibliothèque**|Utiliser VSPerf.lib|  
|**Unicode**|Implémenté en tant que `NameProfileW` \(Unicode\) et `NameProfileA` \(ANSI\).|  
  
## Exemple  
 Le code suivant illustre l'appel de la fonction NameProfile.  L'exemple suppose l'utilisation des macros de chaîne Win32 et des paramètres du compilateur pour ANSI afin de déterminer si le code appelle la fonction compatible ANSI.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Voir aussi  
 [Référence des API du profileur Visual Studio \(Native\)](../profiling/visual-studio-profiler-api-reference-native.md)