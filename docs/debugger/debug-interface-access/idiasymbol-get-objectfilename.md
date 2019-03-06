---
title: IDiaSymbol::get_objectFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 841fe2b1ae6f54b3bc7deea97b335790ca6dac5f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611813"
---
# <a name="idiasymbolgetobjectfilename"></a>IDiaSymbol::get_objectFileName
Récupère le nom de fichier objet.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_objectFilename(
   BSTR *pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Un pointeur vers un `BSTR` qui contient le nom de fichier objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)