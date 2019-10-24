---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9751127007b4e7823cf6d2ae35ed2fe80cb83b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742281"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Récupère les fichiers sources par compiland et nom.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 `pCompiland`

dans Objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le compiland à utiliser comme contexte pour la recherche. Définissez ce paramètre sur `NULL` pour rechercher les fichiers sources dans toutes les compilands.

 `name`

dans Spécifie le nom du fichier source à récupérer. Définissez ce paramètre sur `NULL` pour tous les fichiers sources à récupérer.

 `option`

dans Spécifie les options de comparaison appliquées à la recherche de nom. Les valeurs de l’énumération d' [énumération NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) peuvent être utilisées seules ou en combinaison.

 `ppResult`

à Retourne un objet [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) qui contient une liste des fichiers sources récupérés.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions, énumération](../../debugger/debug-interface-access/namesearchoptions.md)