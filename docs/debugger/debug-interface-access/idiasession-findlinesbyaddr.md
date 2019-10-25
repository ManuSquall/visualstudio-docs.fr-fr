---
title: IDiaSession::findLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 328589df0e662ca27db634017005344d44491275
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742118"
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
Récupère les lignes d’un compiland spécifié qui contiennent une adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLinesByAddr (
    DWORD                 seg,
    DWORD                 offset,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
`seg`

dans Spécifie le composant de section de l’adresse spécifique.

`offset`

dans Spécifie le composant de décalage de l’adresse spécifique.

`length`

dans Spécifie le nombre d’octets de la plage d’adresses à couvrir avec cette requête.

`ppResult`

à Retourne un objet [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste de tous les numéros de ligne qui couvrent la plage d’adresses spécifiée.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple
Cet exemple montre une fonction qui obtient tous les numéros de ligne contenus dans une fonction à l’aide de l’adresse et de la longueur de la fonction.

```C++
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,
                                          IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                seg;
    DWORD                offset;
    ULONGLONG            length;

    if (pFunc->get_addressSection ( &seg ) == S_OK &&
        pFunc->get_addressOffset ( &offset ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)
