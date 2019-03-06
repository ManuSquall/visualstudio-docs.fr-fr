---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21630bea3022769d18748190c2a2d24c0e519a3c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608490"
---
# <a name="datakind"></a>DataKind
Indique la portée d’une valeur de données particulière.

## <a name="syntax"></a>Syntaxe

```C++
enum DataKind {
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
Symbole de données de DataIsUnknown ne peut pas être déterminé.

Élément de données de DataIsLocal est une variable locale.

Élément de données de DataIsStaticLocal est une variable locale statique.

Élément de données de DataIsParam est un paramètre formel.

Élément de données de DataIsObjectPtr est un pointeur d’objet (`this`).

Élément de données de DataIsFileStatic est une variable de portée de fichier.

Élément de données de DataIsGlobal est une variable globale.

Élément de données de DataIsMember est une variable de membre d’objet.

Élément de données de DataIsStaticMember est une variable statique de classe.

Élément de données de DataIsConstant est une valeur constante.

## <a name="remarks"></a>Remarques
Les valeurs dans cette énumération sont retournées par la [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (méthode).

## <a name="requirements"></a>Spécifications
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
