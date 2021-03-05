---
description: Récupère les enregistrements de nombre dans le flux de données de débogage.
title: IDiaEnumDebugStreamData::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get_Count method
ms.assetid: 74ff3a85-3cc2-4aa8-ad9a-7f335b795ed1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ba28ff7deff0135d7a6afddf15c44c92d107ad4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158175"
---
# <a name="idiaenumdebugstreamdataget_count"></a>IDiaEnumDebugStreamData::get_Count
Récupère les enregistrements de nombre dans le flux de données de débogage.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal
- [out, retval] Retourne le nombre d’enregistrements.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)
