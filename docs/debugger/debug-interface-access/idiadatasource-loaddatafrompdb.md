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
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744938"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Ouvre et prépare un fichier de base de données du programme (. pdb) comme source de données de débogage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Paramètres
pdbPath

dans Chemin d’accès au fichier. pdb.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.

|valeur|Description|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier ou de déterminer que le format du fichier n’est pas valide.|
|E_PDB_FORMAT|Tentative d’accès à un fichier avec un format obsolète.|
|E_INVALIDARG|Paramètre non valide.|
|E_UNEXPECTED|La source de données a déjà été préparée.|

## <a name="remarks"></a>Notes
Cette méthode charge les données de débogage directement à partir d’un fichier. pdb.

Pour valider le fichier. pdb par rapport à des critères spécifiques, utilisez la méthode [IDiaDataSource :: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Pour accéder au processus de chargement des données (via un mécanisme de rappel), utilisez la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Pour charger un fichier. pdb directement à partir de la mémoire, utilisez la méthode [IDiaDataSource :: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

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
