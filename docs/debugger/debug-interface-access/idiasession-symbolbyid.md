---
title: IDiaSession::symbolById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 423bf9a1c6d816d17bb36be6a4a84820617234ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864081"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Récupère un symbole par son identificateur unique.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Paramètres
`id`

dans Identificateur unique.

`ppSymbol`

à Retourne un objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole récupéré.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
L’identificateur spécifié est une valeur unique utilisée en interne par le kit de développement logiciel (SDK) DIA pour rendre tous les symboles uniques.

Cette méthode peut être utilisée, par exemple, pour récupérer le symbole représentant le type d’un autre symbole (consultez l’exemple).

## <a name="example"></a>Exemple
Cet exemple récupère un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le type d’un autre symbole. Cet exemple montre comment utiliser la `symbolById` méthode dans la session. Une approche plus simple consiste à appeler la méthode [IDiaSymbol :: get_Type](../../debugger/debug-interface-access/idiasymbol-get-type.md) pour récupérer directement le symbole de type.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
