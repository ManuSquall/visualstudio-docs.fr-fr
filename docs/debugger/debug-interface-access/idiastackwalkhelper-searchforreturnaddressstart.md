---
title: IDiaStackWalkHelper::searchForReturnAddressStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0753cfe2d9ef8b08606185a5f57a3951f54e7de
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741332"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Recherche dans le frame de pile spécifié une adresse de retour à l’adresse de la pile spécifiée ou à proximité de celle-ci.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT searchForReturnAddressStart( 
   IDiaFrameData*  frame,
   ULONGLONG       startAddress,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Paramètres
 `frame`

dans Objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame de pile actuel.

 `startAddress`

dans Adresse mémoire virtuelle à partir de laquelle commencer la recherche.

 `ReturnAddress`

à Retourne l’adresse de retour de la fonction la plus proche à `startAddress`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)