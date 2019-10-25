---
title: EndCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54e8b12f4d3b924b363f42cb098a1d528a8108b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735983"
---
# <a name="endcapture"></a>EndCapture
Termine un intervalle de capture qui a été démarré avec `BeginCapture`.

## <a name="syntax"></a>Syntaxe

```C++
void EndCapture();
```

## <a name="remarks"></a>Notes
 Un intervalle de capture couvre généralement un sous-ensemble d’un frame, par exemple lorsque vous souhaitez capturer des informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture couvre un appel à présent, deux frames d’informations graphiques sont capturés. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présent ; le deuxième Frame couvre l’intervalle entre le premier événement Direct3D après l’appel à present et l’appel à `EndCapture`.

 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer les informations graphiques. autrement dit, vous devez avoir appelé [init](init.md) via une instance de la classe `VsgDbg` avant d’appeler `BeginCapture` ou `EndCapture`.

## <a name="see-also"></a>Voir aussi
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)