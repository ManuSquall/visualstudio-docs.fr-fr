---
title: "Appel des événements de débogueur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4a3870921fab82c92b57b9c64dd30bda109c3bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="calling-debugger-events"></a>Événements de débogueur d’appel
Dans les sessions de débogage se produisent dans un ordre spécifique.  
  
## <a name="discussion"></a>Discussion  
 Pour comprendre le modèle des appels entre le moteur de débogage (DE) et le Gestionnaire de session de débogage (SDM), le texte suivant représente l’ordre d’appel des événements qui se produisent dans une session de débogage classique :  
  
1.  [Attachement et détachement d’un programme](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Lancement du débogueur](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Arrêt d’un programme](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Création d’un point d’arrêt](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Lorsqu’un point d’arrêt est liée ou devenir indépendant](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Erreurs de point d’arrêt](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Atteindre un point d’arrêt](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Suppression d’un point d’arrêt](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Passage en mode arrêt](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Exécution pas à pas en mode arrêt](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Évaluation de l’expression en mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Gestion des exceptions](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)