---
title: Prise en main d’extensibilité du débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8db5e9d42036a7e4b5f1726e2771e143395c5820
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833256"
---
# <a name="get-started-with-debugger-extensibility"></a>Prise en main d’extensibilité du débogueur
Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fournit les informations dont vous avez besoin pour créer et personnaliser les composants du débogueur permet de déboguer des programmes depuis le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage possède des améliorations dérivée de la facilité d’utilisation complète test effectué sur précédente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueurs. Vous pouvez utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage pour parcourir une application multilingue, ou vous pouvez implémenter à la volée, modification des variables pendant le débogage des applications et des solutions de plusieurs langues.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage est exécutée out-of-process avec le programme en cours de débogage et est par conséquent moins intrusif dans l’espace de processus de l’application. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogueur sans affecter votre programme de débogage.  
  
 Utiliser au mieux le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vous devez être familiarisé avec les éléments suivants :  
  
- Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE)  
  
- Le langage de programmation C++  
  
- ATL COM  
  
## <a name="in-this-section"></a>Dans cette section  
 [Feuille de route pour l’extension du débogueur](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Décrit le processus d’implémentation dans votre produit, en fonction de votre compilateur et sa sortie de débogage.  
  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composants, qui incluent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (SH) de débogage.  
  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le moteur de débogage (dé) fonctionne simultanément dans le code, documentation et contextes d’évaluation d’expression. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation pertinente à ce dernier.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.