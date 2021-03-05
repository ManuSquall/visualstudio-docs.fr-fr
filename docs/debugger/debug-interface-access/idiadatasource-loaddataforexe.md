---
description: Ouvre et prépare les données de débogage associées au fichier. exe/. dll.
title: IDiaDataSource::loadDataForExe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ecb7c774314a35f99de41af720b180475e0c55b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158273"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Ouvre et prépare les données de débogage associées au fichier. exe/. dll.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>Paramètres
executable

dans Chemin d’accès au fichier. exe ou. dll.

searchPath

dans Autre chemin d’accès pour rechercher des données de débogage.

pCallback

dans `IUnknown` Interface pour un objet qui prend en charge une interface de rappel de débogage, telle que [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)et/ou les interfaces [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant présente certains des codes d’erreur possibles pour cette méthode.

|Valeur|Description|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier ou le format du fichier n’est pas valide.|
|E_PDB_FORMAT|Tentative d’accès à un fichier avec un format obsolète.|
|E_PDB_INVALID_SIG|La signature ne correspond pas.|
|E_PDB_INVALID_AGE|L’âge ne correspond pas.|
|E_INVALIDARG|Paramètre non valide.|
|E_UNEXPECTED|La source de données a déjà été préparée.|

## <a name="remarks"></a>Notes
L’en-tête debug du fichier. exe/. dll nomme l’emplacement des données de débogage associé.

Cette méthode lit l’en-tête de débogage, puis recherche et prépare les données de débogage. La progression de la recherche peut éventuellement être signalée et contrôlée par le biais de rappels. Par exemple, [IDiaLoadCallback :: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) est appelé lorsque la `IDiaDataSource::loadDataForExe` méthode recherche et traite un répertoire de débogage.

Les interfaces [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) et [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) permettent à l’application cliente de fournir d’autres méthodes de lecture des données à partir du fichier exécutable lorsque le fichier n’est pas accessible directement via des e/s de fichier standard.

Pour charger un fichier. pdb sans validation, utilisez la méthode [IDiaDataSource :: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Pour valider le fichier. pdb par rapport à des critères spécifiques, utilisez la méthode [IDiaDataSource :: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Pour charger un fichier. pdb directement à partir de la mémoire, utilisez la méthode [IDiaDataSource :: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Exemple

```C++
class MyCallBack: public IDiaLoadCallback
{
...
};
MyCallBack callback;
...
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);
if (FAILED(hr))
{
    // Report error
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
