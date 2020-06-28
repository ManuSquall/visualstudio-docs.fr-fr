---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9f8730fb864a70e7f649d5e8b4920d916c07c11
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468489"
---
# <a name="idiadatasource"></a>IDiaDataSource
Initie l’accès à une source de symboles de débogage.

## <a name="syntax"></a>Syntaxe

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDiaDataSource` .

|Méthode|Description|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Récupère le nom de fichier de la dernière erreur de chargement.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Ouvre et prépare un fichier de base de données du programme (. pdb) comme source de données de débogage.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Ouvre et vérifie que le fichier de base de données du programme (. pdb) correspond aux informations de signature fournies. prépare le fichier. pdb en tant que source de données de débogage.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Ouvre et prépare les données de débogage associées au fichier. exe/. dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prépare les données de débogage stockées dans un fichier de base de données du programme (. pdb) accessible via un flux de données en mémoire.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Ouvre une session pour interroger les symboles.|

## <a name="remarks"></a>Remarques
Un appel à l’une des méthodes Load de l' `IDiaDataSource` interface ouvre la source du symbole. Un appel réussi à la méthode [IDiaDataSource :: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) retourne une interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) qui prend en charge l’interrogation de la source de données. Si la méthode Load retourne une erreur liée à un fichier, la valeur de retour de la méthode [IDiaDataSource :: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) contient le nom de fichier associé à l’erreur.

## <a name="notes-for-callers"></a>Notes pour les appelants
Cette interface est obtenue en appelant la `CoCreateInstance` fonction avec l’identificateur de classe `CLSID_DiaSource` et l’ID d’interface de `IID_IDiaDataSource` . L’exemple montre comment cette interface est obtenue.

## <a name="example"></a>Exemple

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2. h

Bibliothèque : diaguids. lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
