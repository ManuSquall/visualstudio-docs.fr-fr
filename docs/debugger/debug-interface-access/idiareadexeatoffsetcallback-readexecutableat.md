---
description: Lit le nombre d’octets spécifié en commençant à l’offset spécifié à partir d’un fichier exécutable.
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9986ba6d493353644d8387b2df36a96cbf542933
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157362"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Lit le nombre d’octets spécifié en commençant à l’offset spécifié à partir d’un fichier exécutable.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Paramètres
 fileOffset

dans Offset dans le fichier exécutable à partir duquel commencer la lecture.

 cbData

dans Nombre d’octets à lire.

 pcbData

à Retourne le nombre d’octets lus.

 data[]

[in, out] Tableau qui est renseigné avec des octets lus à partir du fichier.

## <a name="remarks"></a>Notes
 Cette méthode est appelée par le code de prise en charge de DIA pour charger des octets de données à partir d’un exécutable à l’aide d’un offset de fichier absolu. Cette méthode est appelée pour la prise en charge de la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
