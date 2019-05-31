---
title: Fonction SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a6508b8cfde2f08eb40201973fec899ee11956b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353551"
---
# <a name="sccpopulatedirlist-function"></a>Fonction SccPopulateDirList
Cette fonction détermine les répertoires et (éventuellement) les fichiers sont stockés dans le contrôle de code source, une liste de répertoires à examiner.

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

[in] Le pointeur de contexte de plug-in de contrôle de code source.

 nDirs

[in] Nombre de chemins d’accès de répertoire dans le `lpDirPaths` tableau.

 lpDirPaths

[in] Tableau de chemins de répertoires à examiner.

 pfnPopulate

[in] Fonction de rappel à appeler pour chaque chemin d’accès de répertoire et (éventuellement) nom de fichier dans `lpDirPaths` (consultez [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) pour plus d’informations).

 pvCallerData

[in] Valeur qui doit être transmises sans modification à la fonction de rappel.

 fOptions

[in] Une combinaison de valeurs qui contrôlent la façon dont les répertoires sont traités (consultez la section « Indicateurs PopulateDirList » de [indicateurs de bits utilisés par les commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles).

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|L’opération terminée.|
|SCC_E_UNKNOWNERROR|Une erreur s'est produite.|

## <a name="remarks"></a>Notes
 Uniquement les répertoires et (éventuellement) les noms de fichiers qui sont réellement dans le référentiel de contrôle source sont passés à la fonction de rappel.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codes d’erreur](../extensibility/error-codes.md)