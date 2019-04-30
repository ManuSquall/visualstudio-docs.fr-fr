---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 259ada240d81b87d2d36e12cddcc28efe8d893f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806094"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Il s’agit d’une fonction de rappel donnée à la [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) (fonction) pour mettre à jour une collection de répertoires et (éventuellement) des noms de fichiers qui sont sous contrôle de code source.

 Le `POPDIRLISTFUNC` rappel doit être appelé uniquement pour les répertoires et les noms de fichiers (dans la liste donnée à la `SccPopulateDirList` (fonction)) qui sont réellement sous contrôle de code source.

## <a name="signature"></a>Signature

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Paramètres
 pvCallerData

[in] Valeur d’utilisateur donnée [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` si le nom dans `lpDirectoryOrFileName` est un répertoire ; sinon, le nom est un nom de fichier.

 lpDirectoryOrFileName

[in] Chemin d’accès local complet à un nom de répertoire ou fichier est sous contrôle de code source.

## <a name="return-value"></a>Valeur de retour
 L’IDE retourne un code d’erreur approprié :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Continuer le traitement.|
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|
|SCC_E_xxx|Une erreur de contrôle de source approprié doit arrêter le traitement.|

## <a name="remarks"></a>Notes
 Si le `fOptions` paramètre de la `SccPopulateDirList` fonction contient le `SCC_PDL_INCLUDEFILES` indicateur, puis la liste contient éventuellement les noms de fichiers, ainsi que des noms de répertoires.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Codes d’erreur](../extensibility/error-codes.md)