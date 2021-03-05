---
description: Crée un énumérateur qui contient le même état d’énumération que l’énumérateur du flux de débogage actuel.
title: IDiaEnumDebugStreams::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21b026bd717d20777da1eaa5b815039164abc6b9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158161"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreams** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 `ppenum`

à Retourne un objet [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) qui contient un doublon de l’énumérateur. Les flux ne sont pas dupliqués, mais uniquement l’énumérateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
