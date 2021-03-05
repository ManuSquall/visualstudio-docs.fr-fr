---
description: Crée un énumérateur qui contient le même état d’énumération que l’énumérateur de sources injectées en cours.
title: IDiaEnumInjectedSources::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7752f3b98ff6f4739f92f501297b72501ce0352b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158014"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumInjectedSources** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 `ppenum`

à Retourne un objet [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) qui contient un doublon de l’énumérateur. Les sources injectées ne sont pas dupliquées, mais uniquement l’énumérateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
