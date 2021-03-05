---
description: Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.
title: IDiaStackWalkHelper::frameForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::frameForVA method
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6e4771f899615eb308163c1bc560212a2b4e3cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158900"
---
# <a name="idiastackwalkhelperframeforva"></a>IDiaStackWalkHelper::frameForVA
Récupère le frame de pile qui contient l’adresse virtuelle spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT frameForVA( 
   ULONGLONG        va,
   IDiaFrameData**  ppFrame
);
```

#### <a name="parameters"></a>Paramètres
 `va`

dans Adresse virtuelle pour les données de frame.

 `ppFrame`

à Objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame de pile à l’adresse spécifiée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
