---
title: Fonction SccPopulateDirList (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700557"
---
# <a name="sccpopulatedirlist-function"></a>Fonction SccPopulateDirList
Cette fonction détermine quels répertoires et fichiers (optionnellement) sont stockés dans le contrôle source, compte tenu d’une liste d’annuaires à examiner.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 nDirs (nDirs)

[dans] Nombre de parcours dans `lpDirPaths` le tableau.

 lpDirPaths

[dans] Array de parcours à examiner.

 pfnPopulate

[dans] Fonction de rappel pour appeler pour chaque chemin d’annuaire `lpDirPaths` et (optionnellement) nom de fichier (voir [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) pour plus de détails).

 pvCallerData

[dans] Valeur qui doit être transmise inchangée à la fonction de rappel.

 fOptions

[dans] Une combinaison de valeurs qui contrôlent la façon dont les répertoires sont traités (voir la section "Drapeaux PopulateDirList" de [Bitflags utilisé par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles).

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération s’est terminée correctement.|
|SCC_E_UNKNOWNERROR|Une erreur est survenue.|

## <a name="remarks"></a>Notes
 Seuls les répertoires et les noms de fichiers (optionnellement) qui sont réellement dans le référentiel de contrôle source sont passés à la fonction de rappel.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codes d’erreur](../extensibility/error-codes.md)
