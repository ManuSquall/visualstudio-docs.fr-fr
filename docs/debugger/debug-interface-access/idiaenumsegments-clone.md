---
title: IDiaEnumSegments::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9992b17155601284387981a9b424a77d3d9b5580
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616610"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumSegments** ppenum
);
```

#### <a name="parameters"></a>Paramètres
 ppenum

[out] Retourne un [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) objet qui contient un doublon de l’énumérateur. Les segments ne sont pas dupliquées, uniquement l’énumérateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)