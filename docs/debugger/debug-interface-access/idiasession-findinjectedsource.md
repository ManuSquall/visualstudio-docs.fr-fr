---
description: Récupère une liste de sources qui ont été placées dans le magasin de symboles par des fournisseurs d’attributs ou d’autres composants du processus de compilation.
title: IDiaSession::findInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1604bf91f70f2973dcd394f81569b5ee04e9a99
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147848"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Récupère une liste de sources qui ont été placées dans le magasin de symboles par des fournisseurs d’attributs ou d’autres composants du processus de compilation.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Paramètres
 srcFile

dans Nom du fichier source à rechercher.

 ppResult

à Retourne un objet [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) qui contient une liste de toutes les sources injectées.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
