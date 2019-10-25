---
title: IDiaEnumDebugStreams::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a07669e36d397550c28d1cc4a5de2ad300763e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744741"
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
Récupère un flux de débogage au moyen d’un index ou d’un nom.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item (
    VARIANT                   index,
    IDiaEnumDebugStreamData** stream
);
```

#### <a name="parameters"></a>Paramètres
index

dans Index ou nom du flux de débogage à récupérer. Si un variant entier est utilisé, il doit être compris entre 0 et `count`-1, où `count` est retourné par la méthode [IDiaEnumDebugStreams :: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) .

flux de données

à Retourne un objet [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) qui représente le flux de débogage spécifié.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="example"></a>Exemple

```C++
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,
                                       LONG whichStream)
{
    IDiaEnumDebugStreamData *pStreamData = NULL;
    if (pStreamList != NULL)
    {
        LONG numStreams = 0;
        if (pStreamList->get_count(&numStreams) == S_OK &&
            whichStream >= 0 && whichStream < numStreams)
        {
            VARIANT vIndex;
            vIndex.vt   = VT_I4;
            vIndex.lVal = whichStream;
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)
            {
                std::cerr << "Error retrieving stream " << whichStream << std::endl;
            }
        }
    }
    return(pStreamData);
}
```

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
