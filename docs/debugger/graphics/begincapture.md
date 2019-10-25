---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736144"
---
# <a name="begincapture"></a>BeginCapture
Commence un intervalle de capture qui se termine par `EndCapture`.

## <a name="syntax"></a>Syntaxe

```C++
void BeginCapture();
```

## <a name="remarks"></a>Notes
 Un intervalle de capture couvre généralement un sous-ensemble d’un frame, par exemple lorsque vous souhaitez capturer des informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture couvre un appel à présent, deux frames d’informations graphiques sont capturés. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présent ; le deuxième Frame couvre l’intervalle entre le premier événement Direct3D après l’appel à present et l’appel à `EndCapture`.

 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer les informations graphiques. autrement dit, vous devez avoir appelé [init](init.md) via une instance de la classe `VsgDbg` avant d’appeler `BeginCapture` ou `EndCapture`.

## <a name="see-also"></a>Voir aussi
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)