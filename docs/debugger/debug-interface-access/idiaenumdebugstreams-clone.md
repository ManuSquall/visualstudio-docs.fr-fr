---
title: IDiaEnumDebugStreams::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 105a84b7c4a1b0a43f8f8008cffbebe7b6e23af5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744779"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)