---
title: CV_access_e | Microsoft Docs
description: Obtenir des informations sur le type d’énumération CV_access_e, qui spécifie la portée de la visibilité (niveau d’accès) des membres dans le kit de développement logiciel (SDK) debug interface Access.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39b2cfea273d0b98c178c3cf9bcf3894042f760f
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728694"
---
# <a name="cv_access_e"></a>CV_access_e
Spécifie la portée de la visibilité (niveau d’accès) des variables et des fonctions membres.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Éléments
CV_private membre possède un accès privé.

CV_protected membre a accès protégé.

CV_public membre a un accès public.

## <a name="remarks"></a>Remarques
Le `friend` spécificateur d’accès n’est pas inclus ici, car il est généralement utilisé par les fonctions non-membres qui ont accès aux éléments privés et protégés de la classe. Utilisez la méthode [IDiaSymbol :: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) pour rechercher des symboles avec `SymTagFriend` accès.

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
