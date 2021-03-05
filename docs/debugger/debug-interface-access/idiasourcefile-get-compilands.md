---
description: Récupère un énumérateur de compilands qui ont des numéros de ligne référençant ce fichier.
title: IDiaSourceFile::get_compilands | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2161501bb55385fa9967d6b841b938c1482f20ce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156950"
---
# <a name="idiasourcefileget_compilands"></a>IDiaSourceFile::get_compilands
Récupère un énumérateur de compilands qui ont des numéros de ligne référençant ce fichier.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_compilands ( 
   IDiaEnumSymbols** ppRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `ppRetVal`

à Retourne un objet [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) qui contient une liste de tous les compilands qui ont des numéros de ligne référençant ce fichier.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
