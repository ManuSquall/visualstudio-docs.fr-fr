---
title: IDiaLineNumber::get_sourceFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFile method
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e8d597682b88e30eefb6a1627ebc3e21a7fe7a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864725"
---
# <a name="idialinenumberget_sourcefile"></a>IDiaLineNumber::get_sourceFile
Récupère une référence au fichier source.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_sourceFile ( 
   IDiaSourceFile** pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne un objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représente le fichier source.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)