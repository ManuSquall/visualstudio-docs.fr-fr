---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938532"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
