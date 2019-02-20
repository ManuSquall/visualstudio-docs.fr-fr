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
ms.openlocfilehash: e2503707b8fd5907cd028b7af3e67cd5acd76a00
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227785"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Récupère les informations de numéro de ligne pour les lignes contenues dans une plage d’adresses virtuel spécifié (VA).

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
[in] Spécifie l’adresse utiliser que

`length`  
[in] Spécifie le nombre d’octets de la plage d’adresses pour couvrir cette requête.

`ppResult`  
[out] Retourne un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objet qui contient une liste de tous les nombres qui couvrent la plage d’adresses spécifiée.

## <a name="example"></a>Exemple
Cet exemple montre une fonction qui obtient tous les numéros de ligne contenues dans une fonction à l’aide de l’adresse de fonction virtuel et la longueur.

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
[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
[IDiaSession](../../debugger/debug-interface-access/idiasession.md)
