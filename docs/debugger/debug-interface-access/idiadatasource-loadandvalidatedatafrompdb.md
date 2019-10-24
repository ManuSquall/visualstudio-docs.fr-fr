---
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97afff946827c37ec2f84457016525377977dc8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744999"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Ouvre et vérifie que le fichier de base de données du programme (. pdb) correspond aux informations de signature fournies et prépare le fichier. pdb en tant que source de données de débogage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT loadAndValidateDataFromPdb ( 
   LPCOLESTR pdbPath,
   GUID*     pcsig70,
   DWORD     sig,
   DWORD     age
);
```

#### <a name="parameters"></a>Paramètres
`pdbPath`

dans Chemin d’accès au fichier. pdb.

`pcsig70`

dans Signature GUID à vérifier par rapport à la signature du fichier. pdb. Seuls les fichiers. pdb dans [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] et versions ultérieures ont des signatures GUID.

`sig`

dans Signature 32 bits à vérifier par rapport à la signature du fichier. pdb.

`age`

dans Valeur d’âge à vérifier. L’ancienneté ne correspond pas nécessairement à une valeur d’heure connue, elle est utilisée pour déterminer si un fichier. pdb n’est pas synchronisé avec un fichier. exe correspondant.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.

|valeur|Description|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier ou le format du fichier n’est pas valide.|
|E_PDB_FORMAT|Tentative d’accès à un fichier avec un format obsolète.|
|E_PDB_INVALID_SIG|La signature ne correspond pas.|
|E_PDB_INVALID_AGE|L’âge ne correspond pas.|
|E_INVALIDARG|Paramètre non valide.|
|E_UNEXPECTED|La source de données a déjà été préparée.|

## <a name="remarks"></a>Notes
Un fichier. PDB contient à la fois des valeurs de signature et d’âge. Ces valeurs sont répliquées dans le fichier. exe ou. dll qui correspond au fichier. pdb. Avant de préparer la source de données, cette méthode vérifie que la signature et l’âge du fichier. PDB nommé correspondent aux valeurs fournies.

Pour charger un fichier. pdb sans validation, utilisez la méthode [IDiaDataSource :: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Pour accéder au processus de chargement des données (via un mécanisme de rappel), utilisez la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Pour charger un fichier. pdb directement à partir de la mémoire, utilisez la méthode [IDiaDataSource :: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Exemple

```C++
IDiaDataSource* pSource;  // Previously created data source.
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);
DWORD expectedFileSignature = 0x12345678;
DWORD expectedAge           = 128;

HRESULT hr;
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",
                                          &expectedGUIDSignature,
                                          expectedFileSignature,
                                          expectedAge);
if (FAILED(hr))
{
    // Report an error
}

```

## <a name="see-also"></a>Voir aussi
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
