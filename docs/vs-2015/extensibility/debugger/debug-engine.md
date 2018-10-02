---
title: Moteur de débogage | Microsoft Docs
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
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89f2c2fafb397246a8a2df8dab7d59a361edc11c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504293"
---
# <a name="debug-engine"></a>Moteur de débogage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [moteur de débogage](https://docs.microsoft.com/visualstudio/extensibility/debugger/debug-engine).  
  
Un moteur de débogage (dé) fonctionne avec le système d’exploitation ou un interpréteur pour fournir des services de débogage telles que l’exécution du contrôle des points d’arrêt, évaluation et expression. L’Allemagne est responsable de la surveillance de l’état d’un programme en cours de débogage. Pour cela, l’Allemagne utilise toutes les méthodes sont disponibles dans le runtime pris en charge, si de l’unité centrale ou à partir de l’API fournie par le runtime.  
  
 Par exemple, le common language runtime (CLR) fournit des mécanismes pour surveiller un programme en cours d’exécution via les interfaces ICorDebugXXX. Un dé qui prend en charge le CLR utilise les interfaces ICorDebugXXX appropriées pour suivre un programme de code managé en cours de débogage. Il communique les modifications d’état pour le Gestionnaire de session de débogage (SDM), lequel transmet ces informations à la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
>  Un moteur de débogage cible un runtime spécifique, autrement dit, le système dans lequel le programme débogué s’exécute. Le CLR est le runtime pour le code managé et le runtime Win32 est pour les applications Windows natives. Si la langue que vous créez permettre cibler l’une de ces deux runtimes, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit déjà les moteurs de débogage nécessaires. Il vous suffit d’implémenter est un évaluateur d’expression.  
  
## <a name="debug-engine-operation"></a>Fonctionnement du moteur de débogage  
 Les services de surveillance sont implémentées via les interfaces DE et peuvent provoquer la transition entre les différents modes de fonctionnement du package debug. Pour plus d’informations, consultez [les Modes de fonctionnement](../../extensibility/debugger/operational-modes.md). Il est généralement qu’une seule implémentation DE chaque environnement d’exécution.  
  
> [!NOTE]
>  Bien qu’il existe des implémentations DE distinctes pour Transact-SQL et [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], VBScript et [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] partager un seul DE.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage permet de déboguer les moteurs pour exécuter une des deux manières : soit dans le même processus que le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell ou dans le même processus que le programme cible en cours de débogage. Cette dernière forme se produit généralement lorsque le processus en cours de débogage est en fait un script qui s’exécute sous un interpréteur, et le moteur de débogage doit avoir une connaissance approfondie de l’interpréteur afin de contrôler le script. Notez que dans ce cas, l’interpréteur est en fait un runtime ; moteurs de débogage sont pour les implémentations du runtime spécifique. En outre, l’implémentation d’un seul DE peut être répartie entre les limites de processus et d’ordinateur (par exemple, le débogage distant).  
  
 L’expose DE la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaces de débogage. Toutes les communications sont via COM. Si le dé est chargé dans le processus, out-of-process ou sur un autre ordinateur, il n’affecte pas la communication de composant.  
  
 Le DE fonctionne avec un composant d’évaluateur d’expression pour activer la DE pour cette exécution particulière comprendre la syntaxe des expressions. Le DE fonctionne également avec un composant de gestionnaire de symboles pour accéder aux informations symboliques de débogage générées par le compilateur de langage. Pour plus d’informations, consultez [évaluateur d’Expression](../../extensibility/debugger/expression-evaluator.md) et [fournisseur de symboles](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)

