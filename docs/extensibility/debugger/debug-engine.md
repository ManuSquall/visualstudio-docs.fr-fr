---
title: "Moteur de débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 70e572b73f8474f77a17989c790f2e7336f9d7a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debug-engine"></a>Moteur de débogage
Un moteur de débogage (DE) fonctionne avec l’interpréteur ou à un système d’exploitation pour fournir des services de débogage telles que de l’évaluation d’expression, points d’arrêt et contrôle l’exécution. Le D’est responsable de l’analyse de l’état d’un programme en cours de débogage. Pour cela, le D’utilise toutes les méthodes sont disponibles dans le runtime pris en charge, si de l’unité centrale ou à partir de l’API fournie par le runtime.  
  
 Par exemple, le common language runtime (CLR) fournit des mécanismes permettant de surveiller un programme en cours d’exécution via les interfaces ICorDebugXXX. Un DE qui prend en charge le CLR utilise les interfaces ICorDebugXXX appropriées pour suivre un programme de code managé en cours de débogage. Il communique les changements d’état pour le Gestionnaire de session de débogage (SDM), qui transmet ces informations à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Un moteur de débogage cible un runtime spécifique, autrement dit, le système dans lequel le programme débogué s’exécute. Le CLR est le runtime pour le code managé et le runtime Win32 est pour les applications Windows natives. Si la langue que vous créez permettre cibler l’une de ces deux runtimes, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit déjà des moteurs de débogage nécessaires. Il vous suffit de mettre en œuvre est un évaluateur d’expression.  
  
## <a name="debug-engine-operation"></a>Fonctionnement du moteur de débogage  
 Les services de surveillance sont implémentées via les interfaces DE et peuvent provoquer le package de débogage pour effectuer la transition entre les différents modes de fonctionnement. Pour plus d’informations, consultez [Modes opérationnels](../../extensibility/debugger/operational-modes.md). Il y a généralement qu’une seule implémentation DE par l’environnement d’exécution.  
  
> [!NOTE]
>  Bien qu’il existe des implémentations DE distinctes pour Transact-SQL et [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript et [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] partagent un seul DE.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]débogage permet de déboguer moteurs pour exécuter une des deux manières : soit dans le même processus que le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] du shell, ou dans le même processus que le programme cible en cours de débogage. Cette dernière forme se produit généralement lorsque le processus en cours de débogage est en fait un script qui s’exécute sous un interpréteur et le moteur de débogage doit avoir une connaissance approfondie de l’interpréteur afin de surveiller le script. Notez que dans ce cas, l’interpréteur n’est en fait un runtime ; moteurs de débogage sont pour les implémentations de runtime spécifique. En outre, l’implémentation d’un seul DE peut être répartie entre les limites de processus et de l’ordinateurs (par exemple, le débogage à distance).  
  
 L’expose DE la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaces de débogage. Sont de toutes les communications via COM. Si le D’est chargé dans le processus, out-of-process ou sur un autre ordinateur, il n’affecte pas les communications des composants.  
  
 Le DE fonctionne avec un évaluateur d’expression pour activer le DE pour cette exécution particulier comprendre la syntaxe des expressions. Le DE fonctionne également avec un composant de gestionnaire de symboles pour accéder aux informations symboliques de débogage générées par le compilateur de langage. Pour plus d’informations, consultez [évaluateur d’Expression](../../extensibility/debugger/expression-evaluator.md) et [fournisseur de symbole](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)