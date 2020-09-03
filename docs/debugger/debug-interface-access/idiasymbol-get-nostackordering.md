---
title: IDiaSymbol::get_noStackOrdering | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c82b8c4836d97f02fa84aec500d961911f993df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462790"
---
# <a name="idiasymbolget_nostackordering"></a>IDiaSymbol::get_noStackOrdering
Cette fonction récupère un indicateur qui indique si aucun classement de la pile n’a pu être effectué dans le cadre de la vérification de la mémoire tampon de la pile (option de compilateur[/GS (vérification de la sécurité de la mémoire tampon)](/cpp/build/reference/gs-buffer-security-check) ).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si aucun classement de pile n’a pu être effectué dans le cadre de la vérification de la mémoire tampon de la pile ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (vérification de la sécurité de la mémoire tampon)](/cpp/build/reference/gs-buffer-security-check)