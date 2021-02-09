---
title: IDiaInjectedSource::get_virtualFilename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_virtualFilename method
ms.assetid: b9977075-8fd1-4b11-bfff-d87e9f2586dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78bb087f7e5b66d68e24d66315d9edcd15b06544
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864872"
---
# <a name="idiainjectedsourceget_virtualfilename"></a>IDiaInjectedSource::get_virtualFilename
Récupère le nom donné au code source qui n’est pas un fichier. autrement dit, le code qui a été injecté.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nom donné au code source non-fichier injecté.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)