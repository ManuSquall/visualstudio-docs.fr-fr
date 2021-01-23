---
title: MarkProfile | Microsoft Docs
description: La méthode MarkProfile insère une marque de profil dans le fichier. vsp. Le profilage du thread contenant la fonction MarkProfile doit être ON pour que la marque soit insérée.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecf676c58d8850834ec0c3333196dfb7144f885e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718861"
---
# <a name="markprofile"></a>MarkProfile
La méthode `MarkProfile` insère une marque de profil dans le fichier .*vsp*. Le profilage pour le thread contenant la fonction `MarkProfile` doit être activé pour la marque à insérer.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Paramètres
 `lMarker`

 Marqueur à insérer. La valeur du marqueur doit être supérieure ou égale à zéro.

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour
 La fonction indique la réussite ou l’échec en utilisant l’énumération **PROFILE_COMMAND_STATUS**. La valeur de retour peut être une des suivantes :

|Énumérateur|Description|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Le paramètre est inférieur ou égal à zéro. Ces valeurs sont réservées. La marque et le commentaire ne sont pas enregistrés.|
|MARK_ERROR_MODE_NEVER|Le mode de profilage a été défini sur NEVER quand la fonction a été appelée. La marque et le commentaire ne sont pas enregistrés.|
|MARK_ERROR_MODE_OFF|Le mode de profilage a été défini sur OFF quand la fonction a été appelée. La marque et le commentaire ne sont pas enregistrés.|
|MARK_ERROR_NO_SUPPORT|Pas de prise en charge de marques dans ce contexte. La marque et le commentaire ne sont pas enregistrés.|
|MARK_ERROR_OUTOFMEMORY|La mémoire n’était pas disponible pour enregistrer l’événement. La marque et le commentaire ne sont pas enregistrés.|
|MARK_TEXTTOOLONG|La chaîne dépasse le maximum de 256 caractères. La chaîne de commentaire est tronquée, et la marque et le commentaire sont enregistrés.|
|MARK_OK|MARK_OK est retourné pour indiquer la réussite.|

## <a name="remarks"></a>Notes
 La valeur de la marque est insérée dans le fichier .*vsp* chaque fois que le code s’exécute si le thread contenant la fonction MarkProfile est profilé. Vous pouvez appeler MarkProfile plusieurs fois.

 Les marques de profil sont globales dans l’étendue. Par exemple, une marque de profil insérée dans un thread peut être utilisée pour marquer le début ou la fin d’un segment de données dans n’importe quel thread du fichier .*vsp*.

 L’état du profilage du thread qui contient la fonction de profil de marque doit être Activé lors de l’insertion de marques et de commentaires avec la commande Mark ou des fonctions de l’API (CommentMarkAtProfile, CommentMarkProfile ou MarkProfile).

> [!IMPORTANT]
> La méthode MarkProfile doit être utilisé avec le profilage par instrumentation uniquement.

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informations sur la fonction
 En-tête : déclaré dans *VSPerf.h*

 Bibliothèque d’importation : *VSPerf.lib*

## <a name="example"></a>Exemples
 Le code suivant illustre la fonction MarkProfile.

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur l’API du profileur Visual Studio (natif)](../profiling/visual-studio-profiler-api-reference-native.md)
