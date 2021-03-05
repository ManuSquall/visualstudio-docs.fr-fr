---
description: Récupère le nombre de contributions de section.
title: IDiaEnumSectionContribs::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::get_Count interface
ms.assetid: 94f11de3-9393-4a5c-9814-2e6bdb597f70
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8a0ff3439af3ab973e2cc050e1bb4e5f0d7b41cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159341"
---
# <a name="idiaenumsectioncontribsget_count"></a>IDiaEnumSectionContribs::get_Count
Récupère le nombre de contributions de section.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre de contributions de section.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)
