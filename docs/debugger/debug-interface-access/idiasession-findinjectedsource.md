---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 315c09c29f99d8fe148f9795879193b2cb1f9e49
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465817"
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