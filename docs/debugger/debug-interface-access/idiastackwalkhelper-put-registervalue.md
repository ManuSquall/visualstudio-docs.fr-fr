---
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6a2fd6c7fbca54593a547a1f014fbe7726c814c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464701"
---
# <a name="idiastackwalkhelperput_registervalue"></a>IDiaStackWalkHelper::put_registerValue
Définit la valeur d’un registre.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Paramètres
 `index`

dans Valeur de l’énumération d' [énumération CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) spécifiant le registre dans lequel écrire.

 `NewVal`

dans Nouvelle valeur de registre.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 En dépit de la taille de la valeur, une implémentation doit stocker uniquement ce que le registre contient normalement. Par exemple, un registre 8 bits contiendra uniquement les 8 bits les plus bas de la valeur donnée.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)