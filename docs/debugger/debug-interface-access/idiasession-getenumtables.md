---
title: IDiaSession::getEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b9b229de3818b00379d95a5c19e35c7e83c845e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465425"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Récupère un énumérateur pour toutes les tables contenues dans le magasin de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Paramètres
`ppEnumTables`

à Retourne un objet [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) . Utilisez cette interface pour énumérer les tables dans le magasin de symboles.

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
Cet exemple présente une fonction générale qui utilise la `getEnumTables` méthode pour obtenir un objet énumérateur spécifique. Si l’énumérateur est trouvé, la fonction retourne un pointeur qui peut être casté en l’interface souhaitée ; Sinon, la fonction retourne `NULL` .

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
