---
title: SuspendProfile | Microsoft Docs
description: Découvrez comment la méthode SuspendProfile incrémente le compteur Suspend/Resume pour le niveau de profilage spécifié.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 728aa7c858f8321e3289f2d17e612284f8739f17
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719264"
---
# <a name="suspendprofile"></a>SuspendProfile
La méthode `SuspendProfile` incrémente le compteur Suspend/Resume pour le niveau de profilage spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Paramètres
 `Level`

 Indique le niveau du profil auquel la collecte des données de performances peut être appliquée. Les énumérateurs **PROFILE_CONTROL_LEVEL** suivants peuvent être utilisés pour indiquer un des trois niveaux auxquels la collecte des données de performances peut être appliquée :

|Énumérateur|Description|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Le niveau « global »affecte tous les processus et tous les threads dans l’exécution du profilage.|
|PROFILE_PROCESSLEVEL|Le niveau « processus » affecte tous les threads qui font partie du processus spécifié.|
|PROFILE_THREADLEVEL|Le niveau de profilage « thread » affecte le thread spécifié.|

 `dwId`

 Identificateur du processus ou du thread généré par le système.

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour
 La fonction indique la réussite ou l’échec en utilisant l’énumération **PROFILE_COMMAND_STATUS**. La valeur de retour peut être une des suivantes :

|Énumérateur|Description|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|L’ID d’élément de profilage n’existe pas.|
|PROFILE_ERROR_LEVEL_NOEXIST|Le niveau de profilage spécifié n’existe pas.|
|PROFILE_ERROR_MODE_NEVER|Le mode de profilage a été défini sur NEVER quand la fonction a été appelée.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|L’appel de fonction du profilage, le niveau de profilage ou la combinaison d’appel et de niveau n’est pas encore implémenté.|
|PROFILE_OK|L’appel a réussi.|

## <a name="remarks"></a>Notes
 La valeur initiale du compteur de pauses/reprises est 0. Chaque appel à SuspendProfile ajoute 1 au nombre de Suspend/Resume ; chaque appel à ResumeProfile soustrait 1.

 Quand le nombre de Suspend/Resume est supérieur à 0, l’état Suspend/Resume pour le niveau est ON. Quand le nombre est inférieur ou égal à 0, l’état Suspend/Resume est ON.

 Quand l’état Start/Stop et l’état Suspend/Resume sont tous deux ON, l’état du profilage pour le niveau est ON. Pour qu’un thread soit profilé, les états des niveaux Global, Processus et Thread pour le thread doivent tous être ON.

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Informations sur la fonction
 En-tête : déclaré dans *VSPerf.h*

 Bibliothèque d’importation : *VSPerf.lib*

## <a name="example"></a>Exemples
 L’exemple suivant montre la méthode SuspendProfile. Cet exemple suppose qu’un appel antérieur à StartProfile a été effectué pour le processus ou le thread identifié par [PROFILE_CURRENTID](../profiling/profile-currentid.md).

```cpp
void ExerciseSuspendProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the
    // Suspend/Resume count; each call
    // to ResumeProfile subtracts 1.

    // Variables used to print output
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to SuspendProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = SuspendProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("SuspendProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur l’API du profileur Visual Studio (natif)](../profiling/visual-studio-profiler-api-reference-native.md)
