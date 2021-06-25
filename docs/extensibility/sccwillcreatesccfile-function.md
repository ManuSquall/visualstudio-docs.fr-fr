---
description: Cette fonction détermine si le plug-in de contrôle de code source prend en charge la création du MSSCCPRJ. Fichier SCC pour chacun des fichiers donnés.
title: SccWillCreateSccFile fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f9e6df29b9f44d852c7c84488a3febf590fcc0e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900445"
---
# <a name="sccwillcreatesccfile-function"></a>Fonction SccWillCreateSccFile
Cette fonction détermine si le plug-in de contrôle de code source prend en charge la création du MSSCCPRJ. Fichier SCC pour chacun des fichiers donnés.

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

dans Pointeur de contexte du plug-in de contrôle de code source.

 Nfichiers

dans Le nombre de noms de fichiers inclus dans le `lpFileNames` tableau, ainsi que la longueur du `pbSccFiles` tableau.

 lpFileNames

dans Tableau de noms de fichiers qualifiés complets à vérifier (le tableau doit être alloué par l’appelant).

 pbSccFiles

[in, out] Tableau dans lequel stocker les résultats.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite.|
|SCC_E_INVALIDFILEPATH|L’un des chemins d’accès dans le tableau n’est pas valide.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 Cette fonction est appelée avec une liste de fichiers pour déterminer si le plug-in de contrôle de code source assure la prise en charge dans le fichier MSSCCPRJ. Fichier SCC pour chaque fichier donné (pour plus d’informations sur le fichier MSSCCPRJ. Fichier SCC, consultez [Mssccprj. Fichier SCC](../extensibility/mssccprj-scc-file.md)). Les plug-ins de contrôle de code source peuvent déclarer s’ils ont la possibilité de créer MSSCCPRJ. Fichiers SCC en déclarant `SCC_CAP_SCCFILE` pendant l’initialisation. Le plug-in retourne `TRUE` ou `FALSE` par fichier dans le `pbSccFiles` tableau pour indiquer les fichiers spécifiés qui ont Mssccprj. Prise en charge de SCC. Si le plug-in retourne un code de réussite de la fonction, les valeurs du tableau de retour sont honorées. En cas d’échec, le tableau est ignoré.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
