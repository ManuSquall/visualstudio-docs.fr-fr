---
title: IDiaEnumInjectedSources::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91be2f4f437cfeed30b0741d10bf719ba0ed2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744504"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Récupère une source injectée au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) à récupérer. L’index est la plage allant de 0 à `count`-1, où `count` est retourné par la méthode [IDiaEnumInjectedSources :: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) .

 injectedSource

à Retourne un objet [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) qui représente la source injectée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)