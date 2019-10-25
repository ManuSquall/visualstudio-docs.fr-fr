---
title: IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByVA method
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baf1fc45b69007d3fbe2393ec854ead447fac259
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743809"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
Positionne l’énumérateur en effectuant une recherche par adresse virtuelle (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symbolByVA ( 
   DWORD**      virtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Paramètres
 virtualAddress

dans Adresse virtuelle.

 ppsymbol

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le symbole trouvé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si le symbole est introuvable. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)