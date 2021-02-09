---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bab3bc1c79b6444e75ab75e3d25e8bc395c1be86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857320"
---
# <a name="datakind"></a>DataKind
Indique l’étendue particulière d’une valeur de données.

## <a name="syntax"></a>Syntaxe

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Éléments
Impossible de déterminer le symbole de données DataIsUnknown.

L’élément de données DataIsLocal est une variable locale.

DataIsStaticLocal Data Item est une variable locale statique.

L’élément de données DataIsParam est un paramètre formel.

DataIsObjectPtr Data Item est un pointeur d’objet ( `this` ).

L’élément de données DataIsFileStatic est une variable de portée de fichier.

DataIsGlobal Data Item est une variable globale.

L’élément de données DataIsMember est une variable membre de l’objet.

DataIsStaticMember Data Item est une variable statique de classe.

L’élément de données DataIsConstant est une valeur constante.

## <a name="remarks"></a>Remarques
Les valeurs de cette énumération sont retournées par la méthode [IDiaSymbol :: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
