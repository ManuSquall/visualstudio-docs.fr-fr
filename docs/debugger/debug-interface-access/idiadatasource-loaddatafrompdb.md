---
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb34098f8d69d3c8618c406eff9666d52eace1f2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605599"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
S’ouvre et prépare un fichier de base de données (.pdb) de programme comme une source de données de débogage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Paramètres
pdbPath

[in] Le chemin d’accès au fichier .pdb.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.

|Value|Description|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier, ou déterminé que le fichier a un format non valide.|
|E_PDB_FORMAT|Essaie d’accéder à un fichier avec un format obsolète.|
|E_INVALIDARG|Paramètre non valide.|
|E_UNEXPECTED|Source de données a déjà été préparée.|

## <a name="remarks"></a>Remarques
Cette méthode charge les données de débogage directement à partir d’un fichier .pdb.

Pour valider le fichier .pdb par rapport à des critères spécifiques, utilisez le [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) (méthode).

Pour obtenir l’accès pour le processus de chargement de données (via un mécanisme de rappel), utilisez le [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (méthode).

Pour charger un fichier .pdb directement à partir de la mémoire, utilisez le [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (méthode).

## <a name="example"></a>Exemple

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
