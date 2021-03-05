---
description: Détruit une instance de la classe Vsgdbg,.
title: 'Vsgdbg, :: ~ Vsgdbg, (destructeur) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d90664723695756ebd8acdc7c56bec1fcbd08a31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155224"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
Détruit une instance de la `VsgDbg` classe. Si des informations graphiques sont activement enregistrées, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisées lors de la capture active des informations graphiques sont publiées.

## <a name="syntax"></a>Syntaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Voir aussi
- [VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)
