---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 5a45568ea62a767d06a33c324f0f05a1f697e93f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464981"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
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

dans `IDiaLVarInstance` Objet représentant une instance de variable locale pour laquelle obtenir la valeur.

 `cbDataMax`

dans Nombre maximal d’octets dans la mémoire tampon vers laquelle pointe `pbData` . Il peut s’agir d’un maximum de 8 octets ( `sizeof(ULONGLONG)` ).

 `pcbData`

à Retourne le nombre réel d’octets stockés dans la mémoire tampon.

 `pbData`

à Mémoire tampon à remplir avec des données. Il ne peut pas être `NULL`.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)