---
title: IDiaLineNumber::get_virtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_virtualAddress method
ms.assetid: 9048ef91-a59d-4ad8-90cb-4c13d0989241
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 103d83e3b305e13720b7673dae89f942eb2f692d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743114"
---
# <a name="idialinenumberget_virtualaddress"></a>IDiaLineNumber::get_virtualAddress
Récupère l’adresse virtuelle (VA) du bloc.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’adresse virtuelle du bloc.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)