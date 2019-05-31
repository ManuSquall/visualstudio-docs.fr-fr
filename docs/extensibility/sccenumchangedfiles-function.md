---
title: Fonction SccEnumChangedFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18eab5e5785ea003976c7e291028d5ff964177d8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351866"
---
# <a name="sccenumchangedfiles-function"></a>Fonction SccEnumChangedFiles
Obtenez la liste des fichiers locaux, cette fonction détermine quels fichiers sont différents des versions correspondantes dans la base de données de contrôle de code source.

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

[in] Le pointeur de contexte de plug-in de contrôle de code source.

 hWnd

[in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.

 cFiles

[in] Nombre de noms de fichiers spécifié dans le `lpFileNames` tableau. Spécifie également la taille de `plIsFileDifferent` tableau.

 lpFileNames

[in] Tableau des noms de fichier local à vérifier.

 plIsFileDifferent

[in, out] Tableau de valeurs indiquant l’état de la différence de chaque fichier (tableau doit avoir au moins `cFiles` entrées). Valeur différente de zéro signifie que le fichier est différent.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Opération achevée avec succès.|
|SCC_UNSPECIFIEDERROR|Erreur générique.|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)