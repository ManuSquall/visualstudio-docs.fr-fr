---
description: Récupère la partie d’offset de l’adresse de code pour le frame.
title: IDiaFrameData::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressOffset method
ms.assetid: b68e2e68-6483-4936-bf97-1b0a13cb75e2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 060d6d2fb2c56c0dc3aa8fbb01132a288a2ca45e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157797"
---
# <a name="idiaframedataget_addressoffset"></a>IDiaFrameData::get_addressOffset
Récupère la partie d’offset de l’adresse de code pour le frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne la partie d’offset de l’adresse de code du frame.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
