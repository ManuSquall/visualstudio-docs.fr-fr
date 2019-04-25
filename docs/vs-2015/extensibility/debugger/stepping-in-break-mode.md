---
title: Exécution pas à pas en Mode arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065920"
---
# <a name="stepping-in-break-mode"></a>Exécution pas à pas du mode arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La section suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et qu’il doit parcourir le code :  
  
## <a name="stepping-process"></a>Procédure pas à pas  
  
1. Appelez [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) avec [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments d’exécuter une étape.  
  
2. Lorsque l’étape est terminée, envoyer un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) comme un événement d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
