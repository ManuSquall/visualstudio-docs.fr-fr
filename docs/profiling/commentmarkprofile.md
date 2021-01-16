---
title: CommentMarkProfile | Microsoft Docs
description: Utilisez la fonction CommentMarkProfile pour insérer un marqueur numérique et une chaîne de texte dans le fichier *. vsp* .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e943be08ffd586347ab5de54cb803bcedc8c24d7
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533587"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
La `CommentMarkProfile` fonction insère un marqueur numérique et une chaîne de texte dans le fichier *. vsp* . Pour que la marque et le commentaire soient insérés, le profilage du thread qui contient la fonction `CommentMarkProfile` doit être activé.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Paramètres
 `lMarker`

 Marqueur numérique à insérer. La valeur du marqueur doit être supérieure ou égale à zéro.

 `szComment`

 Pointeur vers la chaîne de texte à insérer. La chaîne ne doit pas comporter plus de 256 caractères, y compris le terminateur NULL.

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

## <a name="remarks"></a>Remarques
 L’état du profilage du thread qui contient la fonction de profil de marque doit être Activé lors de l’insertion de marques et de commentaires avec la commande VSInstr Mark ou avec des fonctions (CommentMarkAtProfile, CommentMarkProfile ou MarkProfile).

 Les marques de profil sont globales dans l’étendue. Par exemple, une marque de profil insérée dans un thread peut être utilisée pour marquer le début ou la fin d’un segment de données dans n’importe quel thread du fichier *. vsp* .

> [!IMPORTANT]
> La méthode CommentMarkProfile peut être utilisé seulement avec l’instrumentation.

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Informations sur la fonction

|Élément|Valeur|
|-|-|
|**En-tête**|Inclure VSPerf.h|
|**Bibliothèque**|Utiliser VSPerf.lib|
|**Unicode**|Implémenté en tant que `CommentMarkProfileW` (Unicode) et `CommentMarkProfileA` (ANSI).|

## <a name="example"></a>Exemple
 Le code suivant illustre l’appel de la fonction CommentMarkProfile. L’exemple suppose l’utilisation de macros de chaîne Win32 et des paramètres de compilateur Unicode pour déterminer si le code appelle la fonction [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)].

```cpp
void ExerciseCommentMarkProfile()
{
    // Declare and initalize variables to pass to
    // CommentMarkProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkProfile(
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur l’API du profileur Visual Studio (natif)](../profiling/visual-studio-profiler-api-reference-native.md)
