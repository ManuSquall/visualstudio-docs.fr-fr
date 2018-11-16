---
title: Exécution pas à pas en Mode arrêt | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4400bcbecce322185ec514e6d05ac9a37e27fdde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749096"
---
# <a name="stepping-in-break-mode"></a>Exécution pas à pas du mode arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La section suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et qu’il doit parcourir le code :  
  
## <a name="stepping-process"></a>Procédure pas à pas  
  
1.  Appelez [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) avec [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments d’exécuter une étape.  
  
2.  Lorsque l’étape est terminée, envoyer un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) comme un événement d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)

