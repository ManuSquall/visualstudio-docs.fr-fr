---
title: Choix d’une stratégie de mise en œuvre de moteur de débogage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 058e3d3087a46de4bb3c5d9b721d3c9111b77526
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203710"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Choisir une stratégie de mise en œuvre de moteur de débogage
Utilisez l’architecture de l’exécution afin de déterminer votre stratégie de mise en œuvre de moteur (dé) débogage. Vous pouvez créer le débogage moteur in-process pour le programme que vous déboguez. Créer le débogage moteur in-process avec le Gestionnaire de débogage de session de Visual Studio (SDM). Ou bien, créez le débogage moteur out-of-process pour chacun d’eux. Les instructions suivantes vous aideront à choisir entre ces trois stratégies.  
  
## <a name="guidelines"></a>Recommandations  
 S’il est possible pour l’Allemagne soit out-of-process pour le SDM et le programme que vous déboguez, il n’existe généralement aucune raison de le faire. Appels au-delà des limites de processus sont relativement lents.  
  
 Déboguer les moteurs sont déjà fournies pour l’environnement d’exécution natif Win32 et pour l’environnement du common language runtime. Si vous devez remplacer le DE pour un environnement, vous devez créer le DE in-process avec le SDM.  
  
 Sinon, vous créez le DE in-process pour le SDM ou processus au programme que vous déboguez. Vous devez prendre en compte si l’évaluateur d’expression de la DE requiert un accès fréquent dans le magasin de symboles du programme. Ou, si le magasin de symboles peut être chargé en mémoire pour un accès rapide. En outre, tenez compte des approches suivantes :  
  
-   S’il n’existe pas de nombre d’appels entre l’évaluateur d’expression et le magasin de symboles, ou si le magasin de symboles peut être lues dans l’espace de mémoire SDM, créez le DE in-process pour le SDM. Vous devez renvoyer le CLSID du moteur de débogage pour le SDM quand elle joint à votre programme. Le SDM utilise ce CLSID pour créer une instance in-process de l’Allemagne.  
  
-   Si le dé doit appeler le programme pour accéder au magasin de symboles, créez le DE in-process avec le programme. Dans ce cas, le programme crée l’instance de l’Allemagne.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)