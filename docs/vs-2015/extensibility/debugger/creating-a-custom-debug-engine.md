---
title: Création d’un moteur de débogage personnalisé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840097"
---
# <a name="creating-a-custom-debug-engine"></a>Création d’un moteur de débogage personnalisé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un moteur de débogage (DE) est un composant qui permet de déboguer des architectures Runtime particulières. Il n’y a généralement qu’une seule implémentation par environnement au moment DE l’exécution.  
  
> [!NOTE]
> Bien qu’il existe des implémentations distinctes de Transact-SQL et JScript, VBScript et JScript partagent un seul DE.  
  
 Un DE fonctionne avec l’interpréteur ou le système d’exploitation pour fournir des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation d’expression. Ces services sont implémentés par le biais des interfaces DE et peuvent entraîner la transition du débogueur entre différents modes opérationnels. Pour plus d’informations, consultez [modes opérationnels](../../extensibility/debugger/operational-modes.md).  
  
 La création d’un DE comprend les étapes suivantes :  
  
1. Inscription d’un à l’aide de Visual Studio  
  
2. Activation d’un programme à déboguer  
  
3. Contrôle d’exécution et évaluation de l’État  
  
4. Envoi des événements  
  
5. Arrêt et détachement  
  
## <a name="in-this-section"></a>Dans cette section  
 [Inscription d’un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explique les étapes nécessaires à l’inscription d’un moteur de débogage avec Visual Studio afin de pouvoir l’utiliser.  
  
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explique qu’avant de pouvoir déboguer un programme, vous devez d’abord lancer le ou l’attacher à un programme existant.  
  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Explique pourquoi le débogage d’une application nécessite l’implémentation des fonctionnalités de contrôle d’exécution.  
  
 [Envoi d’événements](../../extensibility/debugger/sending-events.md)  
 Décrit la communication entre le débogueur et le en tant que modèle d’événement basé sur DCOM.  
  
 [Arrêt et détachement](../../extensibility/debugger/termination-and-detaching.md)  
 Explique comment atteindre un arrêt normal, ce qui signifie qu’il n’y a aucun point d’arrêt, exception, erreur d’exécution ou boucle infinie dans l’application à déboguer.  
  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)  
 Documente l’ordre d’appel des événements qui se produisent dans une session de débogage.  
  
 [Guide pratique pour déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explique comment déboguer un personnalisé DE.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
