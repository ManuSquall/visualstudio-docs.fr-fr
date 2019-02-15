---
title: IDiaDataSource::loadDataForExe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b078e918f399019b2532e7fe3adea220fc09e012
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987546"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
S’ouvre et prépare les données de débogage associées au fichier.exe/.dll.

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
[in] Chemin d’accès au fichier .exe ou .dll.

searchPath  
[in] Autre chemin d’accès pour rechercher des données de débogage.

pCallback  
[in] Un `IUnknown` interface pour un objet qui prend en charge une interface de rappel de débogage, telles que la [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), le [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), et/ou la [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaces.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant présente certains des codes d’erreur possibles pour cette méthode.

|Value|Description|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossible d’ouvrir le fichier ou le fichier a un format non valide.|
|E_PDB_FORMAT|Essaie d’accéder à un fichier avec un format obsolète.|
|E_PDB_INVALID_SIG|Signature ne correspond pas.|
|E_PDB_INVALID_AGE|Âge ne correspond pas.|
|E_INVALIDARG|Paramètre non valide.|
|E_UNEXPECTED|Source de données a déjà été préparée.|

## <a name="remarks"></a>Notes
L’en-tête de débogage du fichier.exe/.dll désigne l’emplacement des données de débogage.

Cette méthode lit l’en-tête de débogage, puis recherche et prépare les données de débogage. La progression de la recherche peut-être, le cas échéant, être signalée et contrôlée via des rappels. Par exemple, le [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) est appelé lorsque le `IDiaDataSource::loadDataForExe` méthode recherche et traite un répertoire de débogage.

Le [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) et [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaces permettent à l’application cliente fournir des méthodes alternatives pour la lecture des données à partir de l’exécutable fichier lorsque le fichier Impossible d’accéder directement par le biais d’e/s de fichier standard.

Pour charger un fichier .pdb sans validation, utilisez la [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) (méthode).

Pour valider le fichier .pdb par rapport à des critères spécifiques, utilisez le [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) (méthode).

Pour charger un fichier .pdb directement à partir de la mémoire, utilisez le [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (méthode).

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
[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)  
[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)  
[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)  
[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
