---
title: "Création d’un fichier du moteur de débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edee6528919cfe28c542be850b9a104188ce403
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-debug-engine"></a>Création d’un moteur de débogage personnalisé
Un moteur de débogage (DE) est un composant qui autorise le débogage d’architectures d’exécution particulières. Il y a généralement qu’une seule implémentation DE par l’environnement d’exécution.  
  
> [!NOTE]
>  Bien qu’il existe des implémentations DE distinctes pour Transact-SQL et JScript, VBScript et JScript partagent un seul DE.  
  
 Un DE fonctionne avec le système interpréteur ou opération pour fournir ces services de débogage comme l’évaluation d’expression, points d’arrêt et contrôle l’exécution. Ces services sont implémentées via les interfaces DE et peuvent entraîner le débogueur pour effectuer la transition entre les différents modes de fonctionnement. Pour plus d’informations, consultez [Modes opérationnels](../../extensibility/debugger/operational-modes.md).  
  
 Création d’un DE comprend les étapes suivantes :  
  
1.  L’inscription d’un DE avec Visual Studio  
  
2.  L’activation d’un programme à déboguer  
  
3.  Évaluation de contrôle et l’état d’exécution  
  
4.  Envoi d’événements  
  
5.  Arrêt et le détachement  
  
## <a name="in-this-section"></a>Dans cette section  
 [Inscription d’un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explique les étapes nécessaires pour inscrire un moteur de débogage avec Visual Studio, afin qu’il peut être utilisé.  
  
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explique qu’avant votre DE peut déboguer un programme, vous devez tout d’abord lancer la DE ou attacher à un programme existant.  
  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Explique pourquoi débogage d’une application requiert l’implémentation des fonctionnalités de contrôle d’exécution.  
  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)  
 Décrit la communication entre le débogueur et DE comme un modèle d’événement en fonction de DCOM.  
  
 [Arrêt et détachement](../../extensibility/debugger/termination-and-detaching.md)  
 Explique comment obtenir une fin normale, ce qui signifie qu’il n’y a aucun points d’arrêt, les exceptions, les erreurs d’exécution ou les boucles infinies dans l’application à déboguer.  
  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)  
 Décrit l’ordre d’appel des événements qui se produisent dans une session de débogage.  
  
 [Guide pratique pour déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explique comment déboguer un personnalisée DE.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)