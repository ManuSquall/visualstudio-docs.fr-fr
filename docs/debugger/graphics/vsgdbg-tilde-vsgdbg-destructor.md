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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734797"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
Détruit une instance de la `VsgDbg` classe. Si des informations graphiques sont activement enregistrées, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisées lors de la capture active des informations graphiques sont publiées.

## <a name="syntax"></a>Syntaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Voir aussi
- [VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)