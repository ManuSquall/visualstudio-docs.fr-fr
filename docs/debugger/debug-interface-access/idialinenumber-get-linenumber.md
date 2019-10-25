---
title: IDiaLineNumber::get_lineNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumber method
ms.assetid: 2dff3fd9-097d-4645-bc1b-cb65ecbc42a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 726f5df7ff898675fc9253b47785c666d435a387
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743201"
---
# <a name="idialinenumberget_linenumber"></a>IDiaLineNumber::get_lineNumber
Récupère le numéro de ligne dans le fichier source.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lineNumber ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le numéro de ligne dans le fichier source.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple

```C++
CComPtr< IDiaLineNumber> pLine;
DWORD linenum;
pLine->get_lineNumber( &linenum );
```

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)