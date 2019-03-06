---
title: IDiaInjectedSource::get_filename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26c68e4f58706fe9d65738e2e58b6ba011999e6a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619249"
---
# <a name="idiainjectedsourcegetfilename"></a>IDiaInjectedSource::get_filename
Récupère le nom de fichier pour la source.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_filename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 pRetVal

[out] Retourne le nom de fichier pour la source.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)