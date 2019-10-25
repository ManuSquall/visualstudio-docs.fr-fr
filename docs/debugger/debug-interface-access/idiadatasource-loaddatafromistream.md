---
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2bcf657b4404ed72059351175d124a9c07abb46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744950"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Prépare les données de débogage stockées dans un fichier de base de données du programme (. pdb) accessible via un flux de données en mémoire.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Paramètres
 pIStream

dans Objet <xref:IStream> représentant le flux de données à utiliser.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.

|valeur|Description|
|-----------|-----------------|
|E_PDB_FORMAT|Tentative d’accès à un fichier avec un format obsolète.|
|E_INVALIDARG|Paramètre non valide.|
|E_UNEXPECTED|La source de données a déjà été préparée.|

## <a name="remarks"></a>Notes
 Cette méthode permet d’obtenir les données de débogage d’un fichier exécutable à partir de la mémoire via un objet <xref:IStream>.

 Pour charger un fichier. pdb sans validation, utilisez la méthode [IDiaDataSource :: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

 Pour valider le fichier. pdb par rapport à des critères spécifiques, utilisez la méthode [IDiaDataSource :: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

 Pour accéder au processus de chargement des données (via un mécanisme de rappel), utilisez la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)