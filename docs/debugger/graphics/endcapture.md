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
ms.openlocfilehash: 0ae024f0d91c980fa8e787b21c93d32a6431203e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895842"
---
# <a name="endcapture"></a>EndCapture
Met fin à un intervalle de capture a été démarré avec `BeginCapture`.

## <a name="syntax"></a>Syntaxe

```C++
void EndCapture();
```

## <a name="remarks"></a>Notes
 Un intervalle de capture couvre généralement un sous-ensemble d’une seule image, par exemple lorsque vous souhaitez capturer les informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture s’étend sur un appel à présenter, deux cadres des informations graphiques sont capturées. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présenter ; la deuxième image s’étend sur l’intervalle entre le premier événement Direct3D après l’appel à présenter et l’appel à `EndCapture`.

 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer des informations graphiques, autrement dit, vous devez appeler [Init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `BeginCapture` ou `EndCapture`.

## <a name="see-also"></a>Voir aussi
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)