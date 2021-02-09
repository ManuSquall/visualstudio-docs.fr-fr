---
title: 'Vsgdbg, :: ~ Vsgdbg, (destructeur) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 53d969e6be772b446598c9c3644582684be488a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861346"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
Détruit une instance de la `VsgDbg` classe. Si des informations graphiques sont activement enregistrées, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisées lors de la capture active des informations graphiques sont publiées.

## <a name="syntax"></a>Syntaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Voir aussi
- [VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)