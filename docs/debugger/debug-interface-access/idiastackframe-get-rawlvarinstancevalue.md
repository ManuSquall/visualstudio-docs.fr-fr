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
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741633"
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

dans Objet `IDiaLVarInstance` représentant une instance de variable locale pour laquelle obtenir la valeur.

 `cbDataMax`

dans Nombre maximal d’octets dans la mémoire tampon vers laquelle pointe `pbData`. Il peut s’agir d’un maximum de 8 octets (`sizeof(ULONGLONG)`).

 `pcbData`

à Retourne le nombre réel d’octets stockés dans la mémoire tampon.

 `pbData`

à Mémoire tampon à remplir avec des données. Il ne peut pas être `NULL`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)