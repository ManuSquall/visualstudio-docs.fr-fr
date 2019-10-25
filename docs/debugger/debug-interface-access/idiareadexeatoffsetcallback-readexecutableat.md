---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d913a229dafb64570728434576716ba396648af3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742833"
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

 cbData

à Retourne le nombre d’octets lus.

 data[]

[in, out] Tableau qui est renseigné avec des octets lus à partir du fichier.

## <a name="remarks"></a>Notes
 Cette méthode est appelée par le code de prise en charge de DIA pour charger des octets de données à partir d’un exécutable à l’aide d’un offset de fichier absolu. Cette méthode est appelée pour la prise en charge de la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)