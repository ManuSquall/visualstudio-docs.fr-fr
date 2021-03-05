---
description: Récupère un élément de données de frame au moyen d’un index.
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c22983881c6f4e7d1bbb8e25ec6030d85411145c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149052"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Récupère un élément de données de frame au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) à récupérer. L’index se trouve dans la plage de 0 à `count` -1, où `count` est retourné par la méthode [IDiaEnumFrameData :: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .

 section

à Retourne un objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente l’élément de données de frame souhaité.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
