---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c96a931593771e381d8f526919a5180da1eb919a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990160"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Capture le reste de l’image actuelle dans le fichier journal de graphiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Notes  
 Si une autre capture est actuellement en cours d’exécution, comme une capture qui a été démarrée par le `BeginCapture` (fonction) — cette capture est terminée et enregistrée dans le journal de graphisme en tant qu’un frame distinct. Immédiatement par la suite, graphics diagnostics commence à capturer le reste de l’image actuelle, qui est également enregistré comme une trame distincte. Fin de l’image actuelle est marquée par un appel à présenter.  
  
 Pour capturer un frame, vous devez préparer votre application pour capturer et enregistrer des informations graphiques, autrement dit, vous devez appeler [Init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Voir aussi  
 [Init](init.md)   
 [BeginCapture](begincapture.md)