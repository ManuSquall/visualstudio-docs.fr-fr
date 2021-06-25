---
title: Moteur de débogage | Microsoft Docs
description: Découvrez comment un moteur de débogage fonctionne avec l’interpréteur ou le système d’exploitation pour fournir des services tels que le contrôle d’exécution, les points d’arrêt et l’évaluation d’expression.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87c4648ed37ef4fad0d79b7048593ff0c5b7d6d0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905707"
---
# <a name="debug-engine"></a>Moteur de débogage
Un moteur DE débogage (DE) fonctionne avec l’interpréteur ou le système d’exploitation pour fournir des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation d’expression. Le DE est chargé de surveiller l’état d’un programme en cours de débogage. Pour ce faire, le service DE utilise les méthodes disponibles dans le runtime pris en charge, que ce soit à partir de l’UC ou des API fournies par le Runtime.

 Par exemple, le common language runtime (CLR) fournit des mécanismes permettant de surveiller un programme en cours d’exécution par le biais des interfaces ICorDebugXXX. Un DE qui prend en charge le CLR utilise les interfaces ICorDebugXXX appropriées pour effectuer le suivi d’un programme de code managé en cours de débogage. Il communique ensuite toutes les modifications d’État au gestionnaire de débogage de session (SDM), qui transfère ces informations à l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Un moteur de débogage cible un Runtime spécifique, c’est-à-dire le système dans lequel le programme en cours de débogage s’exécute. Le CLR est le runtime pour le code managé, tandis que le runtime Win32 est destiné aux applications Windows natives. Si le langage que vous créez peut cibler l’un de ces deux runtimes, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit déjà les moteurs de débogage nécessaires. Tout ce que vous devez implémenter est un évaluateur d’expression.

## <a name="debug-engine-operation"></a>Opération du moteur de débogage
 Les services DE surveillance sont implémentés par le biais des interfaces DE et peuvent entraîner la transition du package de débogage entre différents modes opérationnels. Pour plus d’informations, consultez [modes opérationnels](../../extensibility/debugger/operational-modes.md). Il n’y a généralement qu’une seule implémentation par environnement au moment DE l’exécution.

> [!NOTE]
> Bien qu’il existe des implémentations distinctes pour Transact-SQL et [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] , VBScript et [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] partagent un seul de.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage permet aux moteurs de débogage de s’exécuter de deux manières : dans le même processus que l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interpréteur de commandes ou dans le même processus que le programme cible en cours de débogage. Cette dernière forme se produit généralement lorsque le processus en cours de débogage est en fait un script s’exécutant sous un interpréteur. Le moteur de débogage doit avoir une connaissance approfondie de l’interpréteur afin de surveiller le script. Dans ce cas, l’interpréteur est en fait un Runtime ; les moteurs de débogage sont destinés à des implémentations spécifiques du Runtime. En outre, l’implémentation d’un unique DE peut être fractionnée entre les limites de processus et d’ordinateur (par exemple, le débogage distant).

 Le DE expose les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaces de débogage. Toutes les communications s’effectuent via COM. Si le DE est chargé in-process, out-of-process ou sur un autre ordinateur, il n’affecte pas la communication des composants.

 Le fonctionne avec un composant évaluateur d’expression pour permettre au de ce Runtime particulier de comprendre la syntaxe des expressions. Le DE fonctionne également avec un composant de gestionnaire de symboles pour accéder aux informations de débogage symboliques générées par le compilateur de langage. Pour plus d’informations, consultez [évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md) et fournisseur de [symboles](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Voir aussi
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
- [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)
- [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)
