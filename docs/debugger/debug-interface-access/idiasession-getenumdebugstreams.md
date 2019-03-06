---
title: IDiaSession::getEnumDebugStreams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c962a9bbdebe10b97c47b67b6ce0597027f2c25b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614231"
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
Récupère une séquence énumérée débogage de flux de données.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumDebugStreams ( 
   IDiaEnumDebugStreams** ppEnumDebugStreams
)
```

#### <a name="parameters"></a>Paramètres
 `ppEnumDebugStreams`

[out] Retourne un [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) objet qui contient une liste de flux de débogage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)