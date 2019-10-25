---
title: IDiaEnumSymbolsByAddr::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Clone method
ms.assetid: f4582c69-bc3f-4a26-bcca-b641102b85fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53e6a15221966862031e2c086c6b347cfe373896
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743869"
---
# <a name="idiaenumsymbolsbyaddrclone"></a>IDiaEnumSymbolsByAddr::Clone
Effectue une copie d’un objet.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumSymbolsByAddr** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 ppenum

à Retourne un objet [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) qui contient un doublon de l’énumérateur. Les symboles ne sont pas dupliqués, mais uniquement l’énumérateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)