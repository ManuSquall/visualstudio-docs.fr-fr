---
title: "CommentMarkAtProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode `CommentMarkAtProfile` insère une valeur d'horodatage, une marque numérique et une chaîne de commentaire dans le fichier .vsp.  La valeur d'horodatage peut être utilisée pour synchroniser les événements externes.  Pour que la marque et le commentaire soient insérés, le profilage du thread contenant la fonction CommentMarkAtProfile doit être ON.  
  
## Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### Paramètres  
 `dnTimestamp`  
  
 Entier 64 bits représentant une valeur d'horodatage.  
  
 `lMarker`  
  
 Marqueur numérique à insérer.  Le marqueur doit être supérieur ou égal à 0 \(zéro\).  
  
 `szComment`  
  
 Pointeur sur la chaîne de texte à insérer.  La chaîne doit être inférieure à 256 caractères y compris le terminateur NULL.  
  
## Valeur de propriété\/valeur de retour  
 La fonction indique la réussite ou l'échec en utilisant l'énumération **PROFILE\_COMMAND\_STATUS**.  La valeur de retour peut être l'une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|MARK\_ERROR\_MARKER\_RESERVED|Le paramètre est inférieur ou égal à 0.  Ces valeurs sont réservées.  La marque et le commentaire ne sont pas enregistrés.|  
|MARK\_ERROR\_MODE\_NEVER|La valeur NEVER a été affectée au mode de profilage lors de l'appel à la fonction.  La marque et le commentaire ne sont pas enregistrés.|  
|MARK\_ERROR\_MODE\_OFF|La valeur OFF a été affectée au mode de profilage lors de l'appel à la fonction.  La marque et le commentaire ne sont pas enregistrés.|  
|MARK\_ERROR\_NO\_SUPPORT|Aucune prise en charge de marque dans ce contexte.  La marque et le commentaire ne sont pas enregistrés.|  
|MARK\_ERROR\_OUTOFMEMORY|La mémoire n'était pas disponible pour enregistrer l'événement.  La marque et le commentaire ne sont pas enregistrés.|  
|MARK\_TEXTTOOLONG|La chaîne dépasse le nombre maximum de 256 caractères.  La chaîne de commentaire est tronquée et la marque et le commentaire sont enregistrés.|  
|MARK\_OK|MARK\_OK est retourné en cas de succès.|  
  
## Notes  
 L'état de profilage du thread qui contient la fonction de profil de la marque doit être activé lorsque les marques et les commentaires sont insérés à l'aide de la commande Mark ou des fonctions API \(CommentMarkAtProfile, CommentMarkProfile ou MarkProfile\).  Les marques de profil sont globales dans la portée.  Par exemple, une marque de profil insérée dans un seul thread peut être utilisée pour marquer le début ou la fin d'un segment de données de n'importe quel thread dans le fichier .vsp.  
  
> [!IMPORTANT]
>  Les méthodes CommentMarkAtProfile doivent être utilisées uniquement avec l'instrumentation.  
  
## Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informations sur la fonction  
  
|||  
|-|-|  
|**Header**|Inclure VSPerf.h|  
|**Bibliothèque**|Utiliser VSPerf.lib|  
|**Unicode**|Implémenté en tant que CommentMarkAtProfileW \(Unicode\) et CommentMarkAtProfileA \(ANSI\).|  
  
## Exemple  
 Le code suivant illustre l'utilisation de l'appel de fonction générique CommentMarkAtProfile.  L'exemple suppose l'utilisation des macros de chaîne Win32 et des paramètres du compilateur pour ANSI afin de déterminer si le code appelle la fonction compatible ANSI.  
  
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
  
## Voir aussi  
 [Référence des API du profileur Visual Studio \(Native\)](../profiling/visual-studio-profiler-api-reference-native.md)