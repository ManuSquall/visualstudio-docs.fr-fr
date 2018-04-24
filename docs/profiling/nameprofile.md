---
title: NameProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0b717882e943a37857bbdadf3d318f94b4900dc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="nameprofile"></a>NameProfile
La fonction `NameProfile` affecte une chaîne au processus ou au thread spécifié.  
  
 L’API NameProfile est disponible seulement pour le profilage par instrumentation. L’API NameProfile n’est pas prise en charge pour le profilage par échantillonnage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszName`  
  
 Nom de l’élément de profilage. Un nom n’est pas valide (NameProfileA retournant alors NAME_ERROR_INVALID_NAME) si :  
  
-   Le pointeur passé dans NameProfileA est une valeur NULL  
  
-   Les données de chaîne de pszName commencent par un chiffre  
  
-   Les données de chaîne de pszName contiennent un espace  
  
-   Les données de chaîne de pszName contiennent un des caractères suivants : ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>  
  
 `Level`  
  
 Indique le niveau du profil auquel la collecte des données de performances peut être appliquée. Les valeurs de **PROFILE_CONTROL_LEVEL** suivantes peuvent être utilisés pour indiquer un des trois niveaux auxquels la collecte des données de performances peut être appliquée :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Le niveau « global »affecte tous les processus et tous les threads dans l’exécution du profilage.|  
|PROFILE_PROCESSLEVEL|Le niveau « processus » affecte tous les threads qui font partie du processus spécifié.|  
|PROFILE_THREADLEVEL|Le niveau de profilage « thread » affecte le thread spécifié.|  
  
 `dwId`  
  
 Identificateur de niveau de profilage. Utilisez l’identificateur de processus ou de thread généré par le système.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 La fonction indique la réussite ou l’échec en utilisant l’énumération **PROFILE_COMMAND_STATUS**. La valeur de retour peut être une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|L’élément de profilage spécifié n’existe pas.|  
|NAME_ERROR_INVALID_NAME|Le nom n'est pas valide.|  
|NAME_ERROR_LEVEL_NOEXIST|Le niveau de profilage spécifié n’existe pas.|  
|NAME_ERROR_NO_SUPPORT|L’opération spécifiée n’est pas prise en charge.|  
|NAME_ERROR_OUTOFMEMORY|La mémoire n’était pas disponible pour enregistrer l’événement.|  
|NAME_ERROR_REDEFINITION|Un nom est déjà affecté à l’élément de profil. Le nom de cette fonction est ignoré.|  
|NAME_ERROR_TEXTTRUNCATED|Le texte du nom dépassait 32 caractères, y compris le caractère null, et a donc été tronqué.|  
|NAME_OK|Le nom a été inscrit.|  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez affecter qu’un seul nom à chaque processus ou thread. Une fois qu’un élément de profilage est nommé, les appels suivants à NameProfile pour cet élément sont ignorés.  
  
 Si un même nom est affecté à différents threads ou processus, le rapport comprend les données provenant de tous les éléments de ce niveau portant ce nom.  
  
 Si vous spécifiez un processus ou un thread autre que celui qui est actif, vous devez vérifier qu’il est initialisé et que son exécution a démarré avant de le nommer. Sinon, la méthode NameProfile échoue.  
  
> [!IMPORTANT]
>  Les fonctions d’API CreateProcess() et CreateThread() peuvent retourner avant que le thread ou le processus soit initialisé.  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informations sur la fonction  
  
|||  
|-|-|  
|**Header**|Inclure VSPerf.h|  
|**Bibliothèque**|Utiliser VSPerf.lib|  
|**Unicode**|Implémenté en tant que `NameProfileW` (Unicode) et `NameProfileA` (ANSI).|  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre l’appel de la fonction NameProfile. L’exemple suppose l’utilisation de macros de chaîne Win32 et les paramètres de compilateur pour ANSI afin de déterminer si le code appelle la fonction compatible ANSI.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API du profileur Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)