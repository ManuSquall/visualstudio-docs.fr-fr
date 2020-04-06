---
title: Fonction SccEnumChangedFiles (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700906"
---
# <a name="sccenumchangedfiles-function"></a>Fonction SccEnumChangedFiles
Compte tenu d’une liste de fichiers locaux, cette fonction détermine quels fichiers sont différents des versions correspondantes dans la base de données de contrôle du code source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 cFiles

[dans] Nombre de noms de `lpFileNames` fichiers spécifiés dans le tableau. Spécifie `plIsFileDifferent` également la taille de la gamme.

 lpFileNames

[dans] Array de noms de fichiers locaux à vérifier.

 plIsFileDifferent

[dans, dehors] Array de valeurs indiquant l’état de différence `cFiles` de chaque fichier (tableau doit avoir au moins des entrées). Nonzero signifie que le fichier est différent.

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Opération exécutée avec succès.|
|SCC_UNSPECIFIEDERROR|Erreur générique.|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
