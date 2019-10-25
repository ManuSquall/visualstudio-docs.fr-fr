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
ms.openlocfilehash: 9c15f395e7f4aa576c5f69b0f1c61f37ca808fb6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744614"
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

dans Index de l’objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) à récupérer. L’index se trouve dans la plage 0 à `count`-1, où `count` est retourné par la méthode [IDiaEnumFrameData :: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .

 section

à Retourne un objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente l’élément de données de frame souhaité.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)