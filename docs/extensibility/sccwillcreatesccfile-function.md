---
title: Fonction SccWillCreateSccFile (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700208"
---
# <a name="sccwillcreatesccfile-function"></a>Fonction SccWillCreateSccFile
Cette fonction détermine si le plug-in de contrôle source soutient la création du MSSCCPRJ. Fichier SCC pour chacun des fichiers donnés.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 nFiles

[dans] Le nombre de noms `lpFileNames` de fichiers inclus dans `pbSccFiles` le tableau ainsi que la longueur du tableau.

 lpFileNames

[dans] Une gamme de noms de fichiers entièrement qualifiés à vérifier (tableau doit être attribué par l’appelant).

 pbSccFiles

[dans, dehors] Array dans lequel stocker les résultats.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite.|
|SCC_E_INVALIDFILEPATH|L’un des chemins dans le tableau est invalide.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction est appelée avec une liste de fichiers pour déterminer si le plug-in de contrôle source fournit un soutien dans le MSSCCPRJ. Fichier SCC pour chacun des dossiers donnés (pour plus d’informations sur le MSSCCPRJ. Fichier SCC, voir [MSSCCPRJ. Fichier SCC](../extensibility/mssccprj-scc-file.md)). Les plug-ins de contrôle des sources peuvent déclarer s’ils ont la capacité de créer MSSCCPRJ. Dossiers SCC `SCC_CAP_SCCFILE` en déclarant lors de l’initialisation. Les retours `TRUE` plug-in ou `FALSE` par fichier dans le `pbSccFiles` tableau pour indiquer lequel des fichiers donnés ont MSSCCPRJ. Soutien de la CSC. Si le plug-in renvoie un code de réussite de la fonction, les valeurs du tableau de retour sont honorées. Sur l’échec, le tableau est ignoré.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
