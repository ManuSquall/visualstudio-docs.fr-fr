---
title: Créer une personnalisée moteur de débogage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f071d15b0900fb256fba02502b2e31e72ad2222a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494930"
---
# <a name="creating-a-custom-debug-engine"></a>Création d’un moteur de débogage personnalisé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [création d’un moteur de débogage personnalisé](https://docs.microsoft.com/visualstudio/extensibility/debugger/creating-a-custom-debug-engine).  
  
Un moteur de débogage (dé) est un composant qui permet le débogage d’architectures d’exécution particulières. Il est généralement qu’une seule implémentation DE chaque environnement d’exécution.  
  
> [!NOTE]
>  Bien qu’il existe des implémentations DE distinctes pour Transact-SQL et JScript, VBScript et JScript partagent un seul DE.  
  
 Un DE fonctionne avec le système d’interpréteur ou opération pour fournir ces services de débogage en tant que l’exécution du contrôle des points d’arrêt, évaluation et expression. Ces services sont implémentés via les interfaces DE et peuvent entraîner le débogueur à la transition entre les différents modes de fonctionnement. Pour plus d’informations, consultez [les Modes de fonctionnement](../../extensibility/debugger/operational-modes.md).  
  
 Création d’un dé se compose des étapes suivantes :  
  
1.  L’inscription d’un dé avec Visual Studio  
  
2.  Activation d’un programme à déboguer  
  
3.  Évaluation de contrôle et l’état d’exécution  
  
4.  Envoi d’événements  
  
5.  Arrêt et détachement  
  
## <a name="in-this-section"></a>Dans cette section  
 [Inscription d’un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explique les étapes nécessaires pour inscrire un moteur de débogage avec Visual Studio afin qu’il peut être utilisé.  
  
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explique qu’avant votre dé peut déboguer un programme, vous devez tout d’abord lancer la DE ou attacher à un programme existant.  
  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Explique pourquoi le débogage d’une application nécessite l’implémentation de fonctionnalités de contrôle d’exécution.  
  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)  
 Décrit la communication entre le débogueur et l’Allemagne comme un modèle d’événement basé sur DCOM.  
  
 [Arrêt et détachement](../../extensibility/debugger/termination-and-detaching.md)  
 Explique comment réaliser une fin normale, ce qui signifie qu’il n’y a aucun des points d’arrêt, les exceptions, les erreurs d’exécution ou les boucles infinies dans l’application à déboguer.  
  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)  
 Décrit l’ordre d’appel des événements qui se produisent dans une session de débogage.  
  
 [Guide pratique pour déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explique comment déboguer un dé personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

