---
title: "Choix d’une stratégie de mise en œuvre de moteur de débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fae5211ac270832f07038faafbd6f5bc463d3944
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Choix d’une stratégie de mise en œuvre de moteur de débogage
Utiliser l’architecture de l’exécution pour déterminer votre stratégie de mise en œuvre de débogage moteur (DE). Le moteur de débogage peut-être être créé dans le processus pour le programme débogué, dans le processus sur le Gestionnaire de débogage Visual Studio session (SDM) ou out-of-process pour les deux. Les instructions suivantes doivent vous aider à choisir entre ces trois stratégies.  
  
## <a name="guidelines"></a>Recommandations  
 S’il est possible pour le DE à out-of-process à la fois le SDM et le programme à déboguer, il n’y a généralement aucune raison de le faire. Les appels au-delà des limites de processus sont relativement lents.  
  
 Déboguer les moteurs sont déjà fournies pour l’environnement d’exécution natif Win32 et pour l’environnement du common language runtime. Si vous devez remplacer le DE pour une de ces environnements, vous devez créer le DE in-process avec le SDM.  
  
 Sinon, vous pouvez choisir entre la création de la DE processus pour le SDM ou processus pour le programme à déboguer. Il est important de prendre en compte la nécessité ou non l’évaluateur d’expression de la DE accès fréquent dans le magasin de symboles de programme, et indique si le magasin de symboles peut être chargé en mémoire pour un accès rapide. Considérez également les éléments suivants :  
  
-   S’il n’existe pas de nombreux appels entre l’évaluateur d’expression et le magasin de symboles, ou si le magasin de symboles peut être lus dans l’espace de mémoire SDM, créez le DE in-process pour le SDM. Vous devez retourner le CLSID du moteur de débogage pour le SDM lorsqu’il est joint à votre programme. Le SDM utilise ce CLSID pour créer une instance in-process de le DE.  
  
-   Si le DE doit appeler le programme pour accéder au magasin de symboles, créez le DE in-process avec le programme. Dans ce cas, le programme crée l’instance de la DE.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)