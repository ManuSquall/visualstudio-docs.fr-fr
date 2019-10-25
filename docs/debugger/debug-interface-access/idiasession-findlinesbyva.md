---
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2513825fd2b6f4e6035f9f23295f0c9f00385d0a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742073"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Récupère les informations de numéro de ligne pour les lignes contenues dans une plage d’adresses virtuelles (VA) spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
`va`

dans Spécifie l’adresse en tant que VA.

`length`

dans Spécifie le nombre d’octets de la plage d’adresses à couvrir avec cette requête.

`ppResult`

à Retourne un objet [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste de tous les numéros de ligne qui couvrent la plage d’adresses spécifiée.

## <a name="example"></a>Exemple
Cet exemple montre une fonction qui obtient tous les numéros de ligne contenus dans une fonction à l’aide de l’adresse virtuelle et de la longueur de la fonction.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
