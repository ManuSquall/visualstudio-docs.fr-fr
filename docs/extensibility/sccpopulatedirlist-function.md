---
description: Cette fonction détermine quels répertoires et (éventuellement) les fichiers sont stockés dans le contrôle de code source, à partir d’une liste de répertoires à examiner.
title: SccPopulateDirList fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf2620ff42106be7c858c5104dbf9cb2521252ab
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902356"
---
# <a name="sccpopulatedirlist-function"></a>Fonction SccPopulateDirList
Cette fonction détermine quels répertoires et (éventuellement) les fichiers sont stockés dans le contrôle de code source, à partir d’une liste de répertoires à examiner.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccPopulateDirList(
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

dans Pointeur de contexte du plug-in de contrôle de code source.

 nDirs

dans Nombre de chemins d’accès aux répertoires dans le `lpDirPaths` tableau.

 lpDirPaths

dans Tableau de chemins d’accès aux répertoires à examiner.

 pfnPopulate

dans Fonction de rappel à appeler pour chaque chemin d’accès de répertoire et (éventuellement) nom de fichier dans `lpDirPaths` (consultez [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) pour plus d’informations).

 pvCallerData

dans Valeur qui doit être passée sans modification à la fonction de rappel.

 fOptions

dans Combinaison de valeurs qui contrôlent le mode de traitement des répertoires (consultez la section « indicateurs PopulateDirList » de [indicateurs utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles).

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération s’est terminée correctement.|
|SCC_E_UNKNOWNERROR|Une erreur est survenue.|

## <a name="remarks"></a>Remarques
 Seuls les répertoires et (éventuellement) les noms de fichiers qui se trouvent dans le référentiel de contrôle de code source sont passés à la fonction de rappel.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codes d’erreur](../extensibility/error-codes.md)
