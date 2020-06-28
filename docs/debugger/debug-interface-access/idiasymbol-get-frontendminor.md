---
title: IDiaSymbol::get_frontEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43c3ab40a694dd2ae8623bc3ed6654cf93b0a3ca
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463854"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
Récupère le numéro de version mineure principale.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le numéro de version mineure de front.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Un compilateur se compose généralement de deux éléments principaux : le serveur frontal (l’analyseur), qui gère l’analyse du code source dans un formulaire intermédiaire et un back end (générateur de code), qui convertit le formulaire intermédiaire en assembly. Il n’est pas rare que le serveur frontal ait une version différente de celle du back end.

 Un numéro de version frontale ou de back end est composé de trois parties : \<major> . \<minor> . \<build> , où \<major> est le numéro de version principale, \<minor> est le numéro de version mineure et \<build> est le numéro de Build. Par exemple, 13.10.3077.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)