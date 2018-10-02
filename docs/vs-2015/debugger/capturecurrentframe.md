---
title: CaptureCurrentFrame | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2fcb05d63370f8f40ab09f0978e0f49dbe7d6a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504429"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CaptureCurrentFrame](https://docs.microsoft.com/visualstudio/debugger/graphics/capturecurrentframe).  
  
Capture le reste de l’image actuelle dans le fichier journal de graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Notes  
 Si une autre capture est actuellement en cours d’exécution, comme une capture qui a été démarrée par le `BeginCapture` (fonction) — cette capture est terminée et enregistrée dans le journal de graphisme en tant qu’un frame distinct. Immédiatement par la suite, graphics diagnostics commence à capturer le reste de l’image actuelle, qui est également enregistré comme une trame distincte. Fin de l’image actuelle est marquée par un appel à présenter.  
  
 Pour capturer un frame, vous devez préparer votre application pour capturer et enregistrer des informations graphiques, autrement dit, vous devez appeler [Init](../debugger/init.md) via une instance de la `VsgDbg` classe avant d’appeler `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)



