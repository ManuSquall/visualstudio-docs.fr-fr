---
title: BeginCapture | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d9ac50f2e1f5f92a16a7482a25c9054c2a36f68
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787301"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Commence un intervalle de capture s’achèvera par `EndCapture`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Notes  
 Un intervalle de capture couvre généralement un sous-ensemble d’une seule image, par exemple lorsque vous souhaitez capturer les informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture s’étend sur un appel à présenter, deux cadres des informations graphiques sont capturées. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présenter ; la deuxième image s’étend sur l’intervalle entre le premier événement Direct3D après l’appel à présenter et l’appel à `EndCapture`.  
  
 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer des informations graphiques, autrement dit, vous devez appeler [Init](../debugger/init.md) via une instance de la `VsgDbg` classe avant d’appeler `BeginCapture` ou `EndCapture`.  
  
## <a name="see-also"></a>Voir aussi  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)



