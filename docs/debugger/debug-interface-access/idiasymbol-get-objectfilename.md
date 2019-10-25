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
ms.openlocfilehash: 8e7717e6fbf19fdf8f14e7667db171991319fb3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739636"
---
# <a name="idiasymbolget_objectfilename"></a>IDiaSymbol::get_objectFileName
Récupère le nom du fichier objet.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_objectFilename(
   BSTR *pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers un `BSTR` qui contient le nom du fichier objet.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)