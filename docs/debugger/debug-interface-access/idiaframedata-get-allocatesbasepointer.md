---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8c51b335e0d13752ee2f3c6c68c17b5f2b76a9d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467427"
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

## <a name="remarks"></a>Remarques
 Cette propriété doit être utilisée uniquement par du code qui a fait l’accès à FPO_DATA ou lorsque la chaîne de programme retournée par la méthode [IDiaFrameData :: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) est `NULL` . Dans le cas contraire, la chaîne de programme contient toutes les informations nécessaires pour calculer les valeurs de Registre précédentes.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)