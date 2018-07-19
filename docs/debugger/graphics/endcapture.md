---
title: EndCapture | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27fc4053fdfbfe767e72b9b5511ab3660cd7b4b8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31482189"
---
# <a name="endcapture"></a>EndCapture
Met fin à un intervalle de capture qui a été démarré avec `BeginCapture`.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Notes  
 En règle générale, un intervalle de capture couvre un sous-ensemble d’une seule image, par exemple lorsque vous souhaitez capturer les informations graphiques uniquement sur un certain type d’appel de dessin. Si l’intervalle de capture s’étend sur un appel à présent, les deux images des informations graphiques sont capturées. La première image s’étend sur l’intervalle entre l’appel à `BeginCapture` et l’appel à présenter ; la deuxième image s’étend sur l’intervalle entre le premier événement Direct3D après l’appel à présenter et l’appel à `EndCapture`.  
  
 Pour capturer un intervalle, vous devez préparer votre application pour capturer et enregistrer des informations graphiques, autrement dit, vous devez appeler [Init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `BeginCapture` ou `EndCapture`.  
  
## <a name="see-also"></a>Voir aussi  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)