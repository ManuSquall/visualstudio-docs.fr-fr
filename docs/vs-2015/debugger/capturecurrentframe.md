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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161632"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Capture le reste du frame actuel dans le fichier journal de graphisme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Notes  
 Si une autre capture est actuellement en cours, telle qu’une capture qui a été démarrée par la `BeginCapture` fonction, cette capture est terminée et enregistrée dans le journal de graphisme sous la forme d’un frame distinct. Immédiatement après, Graphics Diagnostics commence à capturer le reste de l’image actuelle, qui est également enregistré sous la forme d’un frame distinct. La fin du frame actuel est marquée par un appel à present.  
  
 Pour capturer un frame, vous devez préparer votre application pour capturer et enregistrer les informations graphiques, autrement dit, vous devez avoir appelé [init](../debugger/init.md) via une instance de la `VsgDbg` classe avant d’appeler `CaptureCurrentFrame` .  
  
## <a name="see-also"></a>Voir aussi  
 [Rein](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
