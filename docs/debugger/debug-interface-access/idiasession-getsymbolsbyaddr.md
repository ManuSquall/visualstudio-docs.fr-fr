---
title: IDiaSession::getSymbolsByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getSymbolsByAddr method
ms.assetid: eafcc757-b488-487d-a063-ad3703ff42e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfe5c047876b6e23c24ad850900cb0c66a4819d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741903"
---
# <a name="idiasessiongetsymbolsbyaddr"></a>IDiaSession::getSymbolsByAddr
Récupère un énumérateur qui recherche les symboles dans l’ordre de leurs adresses.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getSymbolsByAddr( 
   IDiaEnumSymbolsByAddr** ppEnumbyAddr
);
```

#### <a name="parameters"></a>Paramètres
 `ppEnumbyAddr`

à Retourne un objet [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) . Utilisez cette interface pour rechercher des symboles dans le magasin de symboles par emplacement de mémoire.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)