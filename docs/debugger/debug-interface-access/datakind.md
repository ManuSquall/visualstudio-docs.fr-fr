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
ms.openlocfilehash: bf8e59bf79355b4e610091ac8662b8d2a01af322
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318678"
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
DataIsUnknown  
Symbole de données ne peut pas être déterminé.

DataIsLocal  
Élément de données est une variable locale.

DataIsStaticLocal  
Élément de données est une variable locale statique.

DataIsParam  
Élément de données est un paramètre formel.

DataIsObjectPtr  
Élément de données est un pointeur d’objet (`this`).

DataIsFileStatic  
Élément de données est une variable de portée de fichier.

DataIsGlobal  
Élément de données est une variable globale.

DataIsMember  
Élément de données est une variable de membre d’objet.

DataIsStaticMember  
Élément de données est une variable statique de classe.

DataIsConstant  
Élément de données est une valeur constante.

## <a name="remarks"></a>Remarques
Les valeurs dans cette énumération sont retournées par la [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (méthode).

## <a name="requirements"></a>Spécifications
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
[Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
