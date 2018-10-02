---
title: BeginCapture | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f9bc573799ddb5fdd094c7c0e571a88c13b5420
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494231"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [BeginCapture](https://docs.microsoft.com/visualstudio/debugger/graphics/begincapture).  
  
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



