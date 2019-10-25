---
title: 'Vsgdbg, :: ~ Vsgdbg, (destructeur) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734797"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
Détruit une instance de la classe `VsgDbg`. Si des informations graphiques sont activement enregistrées, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisées lors de la capture active des informations graphiques sont publiées.

## <a name="syntax"></a>Syntaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Voir aussi
- [VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)