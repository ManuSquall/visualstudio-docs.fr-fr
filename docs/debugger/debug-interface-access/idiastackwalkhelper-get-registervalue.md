---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fb78b4cbdfa2130731e3847b1a3325ab4cb3eac
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464722"
---
# <a name="idiastackwalkhelperget_registervalue"></a>IDiaStackWalkHelper::get_registerValue
Récupère la valeur d’un registre.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `index`

dans Valeur de l’énumération d' [énumération CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) spécifiant le registre à partir duquel obtenir la valeur.

 `pRetVal`

à Retourne la valeur actuelle du Registre.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 En dépit de la taille du `pRetVal` paramètre, une implémentation doit stocker uniquement ce que le registre contient normalement. Par exemple, un registre 8 bits contient uniquement les 8 bits les plus bas de la valeur donnée. Cette valeur de 8 bits est étendue à 64 bits quand elle est retournée à partir de cette méthode.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)