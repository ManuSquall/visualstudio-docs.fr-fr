---
title: EndCapture | Microsoft Docs
description: Utilisez la méthode EndCapture de la classe Vsgdbg, pour terminer un intervalle de capture qui a été démarré avec BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f7733eb9bed86bc450e4438ce34054312b13db5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880279"
---
# <a name="endcapture"></a>EndCapture
Termine un intervalle de capture qui a été démarré avec `BeginCapture` .

## <a name="syntax"></a>Syntaxe

```C++
void EndCapture();
```

## <a name="remarks"></a>Notes
 Un intervalle de capture couvre généralement un sous-ensemble d’un frame, par exemple lorsque vous souhaitez capturer des informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture couvre un appel à présent, deux frames d’informations graphiques sont capturés. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présent ; la deuxième frame s’étend sur l’intervalle entre le premier événement Direct3D après l’appel à la présente et l’appel à `EndCapture` .

 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer les informations graphiques. autrement dit, vous devez avoir appelé [init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `BeginCapture` ou `EndCapture` .

## <a name="see-also"></a>Voir aussi
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)