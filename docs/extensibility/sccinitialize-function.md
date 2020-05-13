---
title: SccInitialize Fonction (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700641"
---
# <a name="sccinitialize-function"></a>Fonction SccInitialize
Cette fonction est para initialisée par le plug-in de contrôle source et fournit des capacités et des limites à l’environnement de développement intégré (IDE).

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Paramètres
 `ppvContext`

[dans] Le plug-in de contrôle source peut placer un pointeur à sa structure de contexte ici.

 `hWnd`

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 `lpCallerName`

[dans] Le nom du programme appelant le plug-in de contrôle source.

 `lpSccName`

[dans, dehors] Le tampon où le plug-in de contrôle `SCC_NAME_LEN`source met son propre nom (à ne pas dépasser ).

 `lpSccCaps`

[out] Retourne les indicateurs de capacité du plug-in de contrôle de la source.

 `lpAuxPathLabel`

[dans, dehors] Le tampon où le plug-in de contrôle `lpAuxProjPath` source met une chaîne qui décrit le paramètre retourné par `SCC_AUXLABEL_LEN`le [SccOpenProject](../extensibility/sccopenproject-function.md) et le [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (à ne pas dépasser ).

 `pnCheckoutCommentLen`

[out] Retourne la durée maximale permise pour un commentaire de caisse.

 `pnCommentLen`

[out] Retourne la durée maximale permise pour d’autres commentaires.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’initialisation de contrôle de source a réussi.|
|SCC_E_INITIALIZEFAILED|Système n’a pas pu être parasécisé.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer l’opération spécifiée.|
|SCC_E_NONSPECFICERROR|Défaillance non spécifique; système de contrôle des sources n’a pas été parasécé.|

## <a name="remarks"></a>Notes
 L’IDE appelle cette fonction lorsqu’elle charge pour la première fois le plug-in de contrôle source. Il permet à l’IDE de transmettre certaines informations, telles que le nom de l’appelant, au plug-in. L’IDE récupère également certaines informations telles que la longueur maximale autorisée pour les commentaires et les capacités du plug-in.

 Les `ppvContext` points `NULL` à un pointeur. Le plug-in de contrôle de source peut allouer une structure `ppvContext`pour sa propre utilisation et stocker un pointeur à cette structure dans . L’IDE transmettra ce pointeur à toutes les autres fonctions D’API VSSCI, permettant au plug-in d’avoir des informations contextuelles disponibles sans recourir au stockage global et de prendre en charge plusieurs cas du plug-in. Cette structure devrait être deallocated lorsque la [SccUninitialize](../extensibility/sccuninitialize-function.md) est appelée.

 Les `lpCallerName` `lpSccName` paramètres et les paramètres permettent à l’IDE et au plug-in de contrôle source d’échanger des noms. Ces noms peuvent être utilisés simplement pour distinguer entre plusieurs cas, ou ils peuvent effectivement apparaître dans les menus ou les boîtes de dialogue.

 Le `lpAuxPathLabel` paramètre est une chaîne utilisée comme un commentaire pour identifier le chemin du projet auxiliaire qui est stocké dans le fichier de solution et passé au plug-in de contrôle source dans un appel à la [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]utilise la chaîne "SourceSafe Project:"; d’autres plug-ins de contrôle des sources devraient s’abstenir d’utiliser cette chaîne particulière.

 Le `lpSccCaps` paramètre donne au plug-in de contrôle source un endroit pour stocker des bitflags indiquant les capacités du plug-in. (Pour une liste complète des bitflags de capacité, voir [drapeaux de capacité](../extensibility/capability-flags.md)). Par exemple, si le plug-in prévoit d’écrire des résultats dans une fonction de rappel fournie par l’appelant, le plug-in réglerait le bit de capacité SCC_CAP_TEXTOUT. Cela signalerait à l’IDE de créer une fenêtre pour les résultats de contrôle de version.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
