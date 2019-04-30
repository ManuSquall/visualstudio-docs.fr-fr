---
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8d083cea518032c121a5cb9e9213abbbd7eaaf8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829857"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Récupère un élément de données d’image au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Paramètres
 index

[in] Index de la [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet à récupérer. L’index est comprise entre 0 et `count`-1, où `count` est retourné par la [IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) (méthode).

 section

[out] Retourne un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objet représentant l’élément de données d’images souhaitée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)