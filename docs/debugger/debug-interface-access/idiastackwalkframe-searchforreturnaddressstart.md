---
title: IDiaStackWalkFrame::searchForReturnAddressStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 361aa5083f0d3abafc42ddbacf9bee4e464a3336
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464813"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Recherche dans le frame de pile spécifié une adresse de retour à l’adresse spécifiée ou à proximité de celle-ci.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT searchForReturnAddressStart ( 
   IDiaFrameData* frame,
   ULONGLONG      startAddress,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>Paramètres
 `frame`

dans Objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame de pile actuel.

 `startAddress`

dans Adresse mémoire virtuelle à partir de laquelle commencer la recherche.

 `returnAddress`

à Retourne l’adresse de retour de la fonction la plus proche de `startAddress` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)