---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaddb8b71ba96511af3682b442c1e5c8e84a409c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738842"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Récupère le type d’un pointeur de table de base virtuelle.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`pRetVal`|à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui spécifie le type de table de base.|

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Un pointeur de table de base virtuelle (`vbtptr`) est un pointeur masqué dans une [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable qui gère l’héritage à partir de classes de base virtuelles. Une `vbtptr` peut avoir des tailles différentes en fonction des classes héritées.

 Cette méthode retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui peut être utilisé pour déterminer la taille du vbtptr.

## <a name="requirements"></a>spécifications

|Exigence|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)