---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca1b1ec2bea56ad167951ad8b60cf849bd22e315
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742786"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lit le nombre d’octets spécifié en commençant à l’adresse virtuelle relative (RVA) spécifiée à partir du fichier exécutable.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Paramètres
 `relativeVirtualAddress`

dans RVA dans le fichier exécutable à partir duquel commencer la lecture.

 `cbData`

dans Nombre d’octets à lire.

 `pcbData`

à Retourne le nombre d’octets lus.

 `data[]`

[in, out] Tableau qui est rempli avec des octets lus à partir du fichier.

## <a name="remarks"></a>Notes
 Cette méthode est appelée par le code de prise en charge de DIA pour charger des octets de données à partir d’un exécutable à l’aide d’une adresse virtuelle relative. Cette méthode est appelée pour la prise en charge de la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)