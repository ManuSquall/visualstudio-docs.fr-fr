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
ms.openlocfilehash: cd6f5219edf9426067a4431936caa2186604e1cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741538"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Récupère un énumérateur de frame de pile pour les plateformes x86.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Paramètres
 `pHelper`

dans Objet [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) d’assistance.

 `ppEnum`

à Retourne un objet [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) qui contient une liste d’objets [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Pour obtenir une liste de frames de pile sur n’importe quelle autre plateforme, appelez la méthode [IDiaStackWalker :: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)