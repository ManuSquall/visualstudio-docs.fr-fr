---
description: Récupère une séquence énumérée de flux de données de débogage.
title: IDiaSession::getEnumDebugStreams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9711399529fa1afc0eaca70e28a5bae5f2035ba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157027"
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
Récupère une séquence énumérée de flux de données de débogage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumDebugStreams ( 
   IDiaEnumDebugStreams** ppEnumDebugStreams
)
```

#### <a name="parameters"></a>Paramètres
 `ppEnumDebugStreams`

à Retourne un objet [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) qui contient une liste de flux de débogage.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
