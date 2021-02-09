---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5844cc235d604e8433940920eb9244044732d54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855647"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Appelé lorsqu’un répertoire de débogage a été trouvé dans le fichier. exe.

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

[in] `TRUE` Si le répertoire de débogage est lu à partir d’un exécutable (au lieu d’un fichier. dbg).

 `cbData`

dans Nombre d’octets de données dans le répertoire de débogage.

 `data[]`

dans Tableau qui est renseigné avec le répertoire de débogage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le code de retour est généralement ignoré.

## <a name="remarks"></a>Remarques
 La méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) appelle ce rappel lorsqu’il trouve un répertoire de débogage pendant le traitement du fichier exécutable.

 Cette méthode supprime la nécessité pour le client de rétroconcevoir le fichier exécutable et/ou de débogage pour prendre en charge les informations de débogage autres que celles figurant dans le fichier. pdb. Avec ces données, le client peut reconnaître le type d’informations de débogage disponibles et s’il réside dans le fichier exécutable ou le fichier. dbg.

 La plupart des clients n’ont pas besoin de ce rappel, car la `IDiaDataSource::loadDataForExe` méthode ouvre en toute transparence les fichiers. pdb et. dbg si nécessaire pour servir les symboles.

## <a name="see-also"></a>Voir aussi
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)