---
title: IDiaStackWalker::getEnumFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9011f0becd893fa4ca966c40013844b0be47e46d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629389"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Récupère un énumérateur de frame de pile pour x86 plateformes.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Paramètres
 `pHelper`

[in] Le programme d’assistance [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objet.

 `ppEnum`

[out] Retourne un [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) objet qui contient une liste de [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objets.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Remarques
 Pour obtenir une liste de frames de pile sur n’importe quelle autre plateforme, appelez le [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)