---
description: Récupère la version System. Runtime. InteropServices. ComTypes. IEnumVARIANT de l’énumérateur des fichiers sources.
title: IDiaEnumSourceFiles::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get__NewEnum method
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c090406c4e8b9ad6a01c18d4fa17c66038881a3d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159201"
---
# <a name="idiaenumsourcefilesget__newenum"></a>IDiaEnumSourceFiles::get__NewEnum
Récupère la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> version de cet énumérateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

à Retourne l' `IUnknown` interface qui représente la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> version de cet énumérateur.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
