---
title: Choix d’une stratégie de mise en œuvre de moteur de débogage | Microsoft Docs
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
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d2f4d4f907dcabb2aff5457abbbe215507d7601
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734627"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Choix d’une stratégie de mise en œuvre du moteur de débogage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez l’architecture de l’exécution afin de déterminer votre stratégie de mise en œuvre de moteur (dé) débogage. Le moteur de débogage peut-être être créé dans le processus du programme à être débogué, processus au Gestionnaire de débogage Visual Studio session (SDM) ou out-of-process pour chacun d’eux. Les instructions suivantes doivent vous aider à choisir parmi ces trois stratégies.  
  
## <a name="guidelines"></a>Recommandations  
 S’il est possible pour l’Allemagne soit out-of-process à la fois le SDM et le programme à déboguer, il n’existe généralement aucune raison de le faire. Appels au-delà des limites de processus sont relativement lents.  
  
 Déboguer les moteurs sont déjà fournies pour l’environnement d’exécution natif Win32 et pour l’environnement du common language runtime. Si vous devez remplacer le DE pour une de ces environnements, vous devez créer le DE in-process avec le SDM.  
  
 Sinon, vous pouvez choisir entre la création de l’Allemagne dans le processus sur le SDM ou processus pour le programme à déboguer. Il est important de savoir si l’évaluateur d’expression de l’Allemagne doit accéder fréquemment le magasin de symboles de programme, et indique si le magasin de symboles peut être chargé en mémoire pour un accès rapide. Considérez également les points suivants :  
  
-   S’il n’existe pas de nombre d’appels entre l’évaluateur d’expression et le magasin de symboles, ou si le magasin de symboles peut être lues dans l’espace de mémoire SDM, créez le DE in-process pour le SDM. Vous devez renvoyer le CLSID du moteur de débogage pour le SDM quand elle joint à votre programme. Le SDM utilise ce CLSID pour créer une instance in-process de l’Allemagne.  
  
-   Si le dé doit appeler le programme pour accéder au magasin de symboles, créez le DE in-process avec le programme. Dans ce cas, le programme crée l’instance de l’Allemagne.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

