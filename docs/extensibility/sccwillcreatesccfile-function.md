---
title: SccWillCreateSccFile fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ac7657258b79b2e53bee8138bc5b2728f618eac
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720120"
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

dans Le nombre de noms de fichiers inclus dans le tableau `lpFileNames`, ainsi que la longueur du tableau `pbSccFiles`.

 lpFileNames

dans Tableau de noms de fichiers qualifiés complets à vérifier (le tableau doit être alloué par l’appelant).

 pbSccFiles

[in, out] Tableau dans lequel stocker les résultats.

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|Opération réussie.|
|SCC_E_INVALIDFILEPATH|L’un des chemins d’accès dans le tableau n’est pas valide.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Notes
 Cette fonction est appelée avec une liste de fichiers pour déterminer si le plug-in de contrôle de code source assure la prise en charge dans le fichier MSSCCPRJ. Fichier SCC pour chaque fichier donné (pour plus d’informations sur le fichier MSSCCPRJ. Fichier SCC, consultez [Mssccprj. Fichier SCC](../extensibility/mssccprj-scc-file.md)). Les plug-ins de contrôle de code source peuvent déclarer s’ils ont la possibilité de créer MSSCCPRJ. Fichiers SCC en déclarant `SCC_CAP_SCCFILE` pendant l’initialisation. Le plug-in retourne `TRUE` ou `FALSE` par fichier dans le tableau `pbSccFiles` pour indiquer les fichiers spécifiés qui ont MSSCCPRJ. Prise en charge de SCC. Si le plug-in retourne un code de réussite de la fonction, les valeurs du tableau de retour sont honorées. En cas d’échec, le tableau est ignoré.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)