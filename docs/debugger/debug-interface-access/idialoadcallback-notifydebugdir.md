---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce251da3c1cb7b1da00971d46cc0801ad24b8985
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839821"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Appelé lorsqu’un répertoire de débogage a été trouvé dans le fichier .exe.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Paramètres
 `fExecutable`

[in] `TRUE` si le répertoire de débogage est lu à partir d’un fichier exécutable (plutôt qu’un fichier .dbg).

 `cbData`

[in] Nombre d’octets de données dans le répertoire de débogage.

 `data[]`

[in] Tableau qui contient le répertoire de débogage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le code de retour est généralement ignoré.

## <a name="remarks"></a>Notes
 Le [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) méthode appelle ce rappel lorsqu’il détecte un répertoire de débogage lors du traitement du fichier exécutable.

 Cette méthode supprime la nécessité pour le client rétroconcevoir le fichier exécutable et/ou de débogage pour prendre en charge les informations de débogage autre que celle trouvée dans le fichier .pdb. Avec ces données, le client peut reconnaître le type d’informations de débogage disponibles et qu’il réside dans le fichier exécutable ou le fichier .dbg.

 La plupart des clients ne seront pas besoin de ce rappel, car le `IDiaDataSource::loadDataForExe` méthode en toute transparence les fichiers .pdb et .dbg lorsque cela est nécessaire pour traiter les symboles s’ouvre.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)