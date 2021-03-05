---
description: 'IDiaFrameData :: get_allocatesBasePointer récupère un indicateur qui indique si le pointeur de base est alloué pour le code de cette plage d’adresses.'
title: IDiaFrameData::get_allocatesBasePointer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fce5e5dbd12be7bae6ba1937b30c8a5d62de3ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157747"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Récupère un indicateur qui indique si le pointeur de base est alloué pour le code de cette plage d’adresses. Cette méthode est déconseillée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si un pointeur de base est alloué ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette propriété doit être utilisée uniquement par du code qui a fait l’accès à FPO_DATA ou lorsque la chaîne de programme retournée par la méthode [IDiaFrameData :: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) est `NULL` . Dans le cas contraire, la chaîne de programme contient toutes les informations nécessaires pour calculer les valeurs de Registre précédentes.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
