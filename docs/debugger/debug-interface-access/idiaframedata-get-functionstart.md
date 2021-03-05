---
description: 'IDiaFrameData :: get_functionStart récupère un indicateur qui indique si le bloc contient le point d’entrée d’une fonction.'
title: IDiaFrameData::get_functionStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 996442dfbd615b7a1d4e73e2191ced36218570b4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148562"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
Récupère un indicateur qui signale si le bloc contient le point d’entrée d’une fonction.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le bloc contient le point d’entrée ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il est possible qu’un frame de pile ne soit pas le début d’une fonction, car le frame représente une méthode ou une fonction inline insérée dans une fonction.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
