---
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28e2f0ec5f176ab32e6bfed1e959f68c04550f67
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464855"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Récupère un énumérateur de frame de pile pour un type de plateforme spécifique.

## <a name="syntax"></a>Syntaxe

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Paramètres
 `cpuid`

dans Valeur de l’énumération d' [énumération CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) , en spécifiant le type de plateforme.

 `pHelper`

dans Objet [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) d’assistance.

 `ppEnum`

à Retourne un objet [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) contenant une liste d’objets [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Pour obtenir une liste de frames de pile uniquement pour la plateforme x86, appelez la méthode [IDiaStackWalker :: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)