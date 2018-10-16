---
title: CommentMarkAtProfile | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9a3f1c33deb1cae18b43d43af6ded9a8ea2c8ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268435"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La méthode `CommentMarkAtProfile` insère une valeur d’horodatage, une marque numérique et une chaîne de commentaire dans le fichier .vsp. La valeur d’horodatage peut être utilisée pour synchroniser des événements externes. Pour que la marque et le commentaire soient insérés, le profilage du thread qui contient la fonction CommentMarkAtProfile doit être activé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dnTimestamp`  
  
 Entier de 64 bits qui représente une valeur d’horodatage.  
  
 `lMarker`  
  
 Marqueur numérique à insérer. La valeur du marqueur doit être supérieure ou égale à zéro.  
  
 `szComment`  
  
 Pointeur vers la chaîne de texte à insérer. La chaîne ne doit pas comporter plus de 256 caractères, y compris le terminateur NULL.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 La fonction indique la réussite ou l’échec en utilisant l’énumération **PROFILE_COMMAND_STATUS**. La valeur de retour peut être une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Le paramètre est inférieur ou égal à zéro. Ces valeurs sont réservées. La marque et le commentaire ne sont pas enregistrés.|  
|MARK_ERROR_MODE_NEVER|Le mode de profilage a été défini sur NEVER quand la fonction a été appelée. La marque et le commentaire ne sont pas enregistrés.|  
|MARK_ERROR_MODE_OFF|Le mode de profilage a été défini sur OFF quand la fonction a été appelée. La marque et le commentaire ne sont pas enregistrés.|  
|MARK_ERROR_NO_SUPPORT|Pas de prise en charge de marques dans ce contexte. La marque et le commentaire ne sont pas enregistrés.|  
|MARK_ERROR_OUTOFMEMORY|La mémoire n’était pas disponible pour enregistrer l’événement. La marque et le commentaire ne sont pas enregistrés.|  
|MARK_TEXTTOOLONG|La chaîne dépasse le maximum de 256 caractères. La chaîne de commentaire est tronquée, et la marque et le commentaire sont enregistrés.|  
|MARK_OK|MARK_OK est retourné pour indiquer la réussite.|  
  
## <a name="remarks"></a>Notes  
 L’état du profilage du thread qui contient la fonction de profil de marque doit être Activé lors de l’insertion de marques et de commentaires avec la commande Mark ou des fonctions de l’API (CommentMarkAtProfile, CommentMarkProfile ou MarkProfile). Les marques de profil sont globales dans l’étendue. Par exemple, une marque de profil insérée dans un thread peut être utilisée pour marquer le début ou la fin d’un segment de données dans n’importe quel thread dans le fichier .vsp.  
  
> [!IMPORTANT]
>  La méthode CommentMarkAtProfile doit être utilisée seulement avec une instrumentation.  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informations sur la fonction  
  
|||  
|-|-|  
|**Header**|Inclure VSPerf.h|  
|**Bibliothèque**|Utiliser VSPerf.lib|  
|**Unicode**|Implémenté en tant que CommentMarkAtProfileW (Unicode) et CommentMarkAtProfileA (ANSI).|  
  
## <a name="example"></a>Exemple  
 Le code suivant illustre l’utilisation de l’appel de fonction générique CommentMarkAtProfile. L’exemple suppose l’utilisation de macros de chaîne Win32 et les paramètres de compilateur pour ANSI afin de déterminer si le code appelle la fonction compatible ANSI.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API du profileur Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)



