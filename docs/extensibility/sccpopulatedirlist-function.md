---
title: SccPopulateDirList fonction) | Microsoft Docs
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
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720897"
---
# <a name="sccpopulatedirlist-function"></a>Fonction SccPopulateDirList
Cette fonction détermine quels répertoires et (éventuellement) les fichiers sont stockés dans le contrôle de code source, à partir d’une liste de répertoires à examiner.

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

dans Pointeur de contexte du plug-in de contrôle de code source.

 nDirs

dans Nombre de chemins d’accès aux répertoires dans le tableau de `lpDirPaths`.

 lpDirPaths

dans Tableau de chemins d’accès aux répertoires à examiner.

 pfnPopulate

dans Fonction de rappel à appeler pour chaque chemin d’accès de répertoire et (facultatif) nom de fichier dans `lpDirPaths` (pour plus d’informations, consultez [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) ).

 pvCallerData

dans Valeur qui doit être passée sans modification à la fonction de rappel.

 fOptions

dans Combinaison de valeurs qui contrôlent le mode de traitement des répertoires (consultez la section « indicateurs PopulateDirList » de [indicateurs utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) pour les valeurs possibles).

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|L’opération a été correctement effectuée.|
|SCC_E_UNKNOWNERROR|Une erreur s'est produite.|

## <a name="remarks"></a>Notes
 Seuls les répertoires et (éventuellement) les noms de fichiers qui se trouvent dans le référentiel de contrôle de code source sont passés à la fonction de rappel.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Codes d’erreur](../extensibility/error-codes.md)