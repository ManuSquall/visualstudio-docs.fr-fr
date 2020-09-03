---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5a9f25c3913519b50131ec5860e127bef3ddc11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467266"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Récupère la chaîne de programme utilisée pour calculer le jeu de registres avant l’appel à la fonction active.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne la chaîne de programme.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La chaîne de programme est une séquence de macros qui est interprétée afin d’établir le prologue. Par exemple, un frame de pile classique peut utiliser la chaîne de programme `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Le format est la notation polonaise inverse, où les opérateurs suivent les opérandes. `T0` représente une variable temporaire sur la pile. Cet exemple effectue les étapes suivantes :

1. Déplacer le contenu du Registre `ebp` vers `T0` .

2. Ajoutez `4` à la valeur dans `T0` pour produire une adresse, obtenez la valeur à partir de cette adresse et stockez la valeur dans Register `eip` .

3. Obtient la valeur de l’adresse stockée dans `T0` et stocke cette valeur dans Register `ebp` .

4. Ajoutez `8` à la valeur dans `T0` et stockez cette valeur dans Register `esp` .

   Notez que la chaîne de programme est spécifique au processeur et à la Convention d’appel définie pour la fonction représentée par le frame de pile actuel.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)