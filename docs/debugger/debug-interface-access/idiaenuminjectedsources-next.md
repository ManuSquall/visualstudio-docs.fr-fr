---
title: IDiaEnumInjectedSources::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aea793f33eb78ee1637d7f22eb46ba34514e0e8f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645041"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Récupère un nombre spécifié de sources injectés dans la séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG                celt,
   IDiaInjectedSource** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

[in] Le nombre de sources injectés dans l’énumérateur à récupérer.

 rgelt

[out] Retourne un tableau de [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objets qui représentent les sources injectés souhaités.

 pceltFetched

[out] Retourne le nombre de sources injectés dans l’énumérateur extraite.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il existe plus aucun injectées sources. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)