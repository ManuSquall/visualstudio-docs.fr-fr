---
title: BeginCapture | Microsoft Docs
description: Utilisez la méthode BeginCapture de la classe Vsgdbg, pour commencer un intervalle de capture qui se termine par EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9e002a66ec3ec121a4cdc20ffb9ce59c1ed9dc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874572"
---
# <a name="begincapture"></a>BeginCapture
Commence un intervalle de capture qui se termine par `EndCapture` .

## <a name="syntax"></a>Syntaxe

```C++
void BeginCapture();
```

## <a name="remarks"></a>Notes
 Un intervalle de capture couvre généralement un sous-ensemble d’un frame, par exemple lorsque vous souhaitez capturer des informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture couvre un appel à présent, deux frames d’informations graphiques sont capturés. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présent ; la deuxième frame s’étend sur l’intervalle entre le premier événement Direct3D après l’appel à la présente et l’appel à `EndCapture` .

 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer les informations graphiques. autrement dit, vous devez avoir appelé [init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `BeginCapture` ou `EndCapture` .

## <a name="see-also"></a>Voir aussi
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)