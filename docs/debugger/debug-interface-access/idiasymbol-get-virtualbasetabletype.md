---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 858f149abb0bec444c43ea706e638def4ff930ce
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461440"
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

## <a name="remarks"></a>Remarques
 Un pointeur de table de base virtuelle ( `vbtptr` ) est un pointeur masqué dans un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable qui gère l’héritage à partir de classes de base virtuelles. Un `vbtptr` peut avoir des tailles différentes en fonction des classes héritées.

 Cette méthode retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui peut être utilisé pour déterminer la taille du vbtptr.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)