---
title: POPDIRLISTFUNC - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702080"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Il s’agit d’une fonction de rappel donnée à la fonction [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) pour mettre à jour une collection d’annuaires et (optionnellement) noms de fichiers pour savoir qui sont sous contrôle source.

 Le `POPDIRLISTFUNC` rappel ne doit être appelé que pour les répertoires `SccPopulateDirList` et les noms de fichiers (dans la liste donnée à la fonction) qui sont en fait sous contrôle source.

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

[dans] Valeur utilisateur donnée à [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder (en)

[dans] `TRUE` si le `lpDirectoryOrFileName` nom est un répertoire; sinon le nom est un nom de fichier.

 lpDirectoryOrFileName

[dans] Voie locale complète vers un répertoire ou un nom de fichier qui est sous contrôle de code source.

## <a name="return-value"></a>Valeur retournée
 L’IDE renvoie un code d’erreur approprié :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Continuer le traitement.|
|SCC_I_OPERATIONCANCELED|Arrêter le traitement.|
|SCC_E_xxx|Toute erreur de contrôle source appropriée doit cesser le traitement.|

## <a name="remarks"></a>Notes
 Si `fOptions` le paramètre de la `SccPopulateDirList` fonction contient le `SCC_PDL_INCLUDEFILES` drapeau, alors la liste contiendra peut-être des noms de fichiers ainsi que des noms d’annuaire.

## <a name="see-also"></a>Voir aussi
- [Fonctions de rappel mises en œuvre par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Codes d’erreur](../extensibility/error-codes.md)
