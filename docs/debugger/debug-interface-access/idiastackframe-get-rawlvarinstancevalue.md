---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8ad236307360a96f64999313764424305980fc9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624020"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Cette méthode récupère la valeur de la variable locale spécifiée comme octets bruts.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Paramètres
 `pInstance`

[in] Un `IDiaLVarInstance` objet représentant une instance d’une variable locale pour obtenir la valeur de.

 `cbDataMax`

[in] Nombre maximal d’octets dans la mémoire tampon vers laquelle pointe `pbData`. Cela peut être un maximum de 8 octets (`sizeof(ULONGLONG)`).

 `pcbData`

[out] Retourne le nombre réel d’octets stockés dans la mémoire tampon.

 `pbData`

[out] Une mémoire tampon à remplir avec des données. Il ne peut pas être `NULL`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)