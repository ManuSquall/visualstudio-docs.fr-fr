---
title: EndCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a451746cae978f141b30fb7295a82310e04367c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197097"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Termine un intervalle de capture qui a été démarré avec `BeginCapture` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>Notes  
 Un intervalle de capture couvre généralement un sous-ensemble d’un frame, par exemple lorsque vous souhaitez capturer des informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture couvre un appel à présent, deux frames d’informations graphiques sont capturés. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présent ; la deuxième frame s’étend sur l’intervalle entre le premier événement Direct3D après l’appel à la présente et l’appel à `EndCapture` .  
  
 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer les informations graphiques. autrement dit, vous devez avoir appelé [init](../debugger/init.md) via une instance de la `VsgDbg` classe avant d’appeler `BeginCapture` ou `EndCapture` .  
  
## <a name="see-also"></a>Voir aussi  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
