---
description: 'IDiaStackFrame :: get_maxStack récupère le nombre maximal d’octets ayant fait l’objet d’un push sur la pile dans le frame.'
title: IDiaStackFrame::get_maxStack | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7668d07db8717892951110b181ae2baa5cd7d153
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147449"
---
# <a name="idiastackframeget_maxstack"></a>IDiaStackFrame::get_maxStack
Récupère le nombre maximal d’octets ayant fait l’objet d’un push sur la pile dans le frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre maximal d’octets ayant fait l’objet d’un push sur la pile.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
