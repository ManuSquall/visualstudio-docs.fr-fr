---
title: IDiaEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20bd652437f0c1765686afc1d93a81bc9110236d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829119"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Énumère les différents tableaux contenus dans la source de données.

## <a name="syntax"></a>Syntaxe

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDiaEnumTables`.

|Méthode|Description|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Récupère le [IEnumVARIANT Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) version de cet énumérateur.|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Récupère le nombre de tables.|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Récupère un tableau au moyen d’un index ou un nom.|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Récupère un nombre spécifié de tables dans la séquence d’énumération.|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignore un nombre spécifié de tables dans une séquence d’énumération.|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Réinitialise une séquence d’énumération au début.|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|

## <a name="remarks"></a>Notes

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
Obtenez cette interface en appelant le [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) (méthode).

## <a name="example"></a>Exemple
Cet exemple montre comment obtenir le `IDiaEnumTables` interface à partir d’une session. Pour obtenir un exemple plus complet de l’utilisation de tables, consultez le [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    // Do something with table
}
```

## <a name="requirements"></a>Configuration requise
En-tête : Dia2.h

Bibliothèque : diaguids.lib

DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
