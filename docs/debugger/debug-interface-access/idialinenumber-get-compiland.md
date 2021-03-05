---
description: Récupère une référence au symbole du compiland qui a contribué aux octets du texte de l’image.
title: IDiaLineNumber::get_compiland | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2700ffb00c14a0f9f62f274157ffadecb0abee26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157594"
---
# <a name="idialinenumberget_compiland"></a>IDiaLineNumber::get_compiland
Récupère une référence au symbole du compiland qui a contribué aux octets du texte de l’image.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) pour le compiland qui a contribué aux octets du texte de l’image.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
