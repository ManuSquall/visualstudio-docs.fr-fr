---
description: Récupère le type d’un pointeur de table de base virtuelle.
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67affafd1984f811432a0b69fdcdfec0521e377
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155515"
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

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Un pointeur de table de base virtuelle ( `vbtptr` ) est un pointeur masqué dans un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable qui gère l’héritage à partir de classes de base virtuelles. Un `vbtptr` peut avoir des tailles différentes en fonction des classes héritées.

 Cette méthode retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui peut être utilisé pour déterminer la taille du vbtptr.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
