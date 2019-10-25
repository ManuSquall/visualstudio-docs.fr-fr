---
title: IDiaEnumTables::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get__NewEnum method
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07fddc9729063009181e3855a30fd4ee825f14d9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743763"
---
# <a name="idiaenumtablesget__newenum"></a>IDiaEnumTables::get__NewEnum
Récupère la version <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de cet énumérateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’interface `IUnknown` qui représente la version <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de cet énumérateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)