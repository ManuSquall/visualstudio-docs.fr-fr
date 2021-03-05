---
description: Récupère un indicateur qui signale si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour un C++ AMP Accelerator.
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8da1e0e8672fb0c10769ca448556f0007fe44014
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147302"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Récupère un indicateur qui signale si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour un C++ AMP Accelerator.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Pointeur vers un `BOOL` qui indique si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour un C++ amp Accelerator. Si `TRUE` la valeur est, les `get_baseDataSlot` `get_baseDataOffset` méthodes et peuvent être utilisées pour obtenir les informations relatives à l’emplacement de stockage de la variable.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
