---
title: Moteur Debug (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739068"
---
# <a name="debug-engine"></a>Moteur Debug
Un moteur de déboguer (DE) fonctionne avec l’interprète ou le système d’exploitation pour fournir des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation de l’expression. Le DE est responsable de la surveillance de l’état d’un programme en cours de déboisation. Pour ce faire, le DE utilise toutes les méthodes qui s’y trouvent dans le temps d’exécution pris en charge, que ce soit à partir du processeur ou des API fournies par le temps d’exécution.

 Par exemple, le temps d’exécution de langue commun (CLR) fournit des mécanismes pour surveiller un programme en cours d’exécution à travers les interfaces ICorDebugXXX. Un DE qui prend en charge le CLR utilise les interfaces ICorDebugXXXX pour garder une trace d’un programme de code géré étant débogé. Il communique ensuite tout changement d’état au gestionnaire de débogé de session [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (SDM), qui transmet ces informations à l’IDE.

> [!NOTE]
> Un moteur de débogé cible un temps de course spécifique, c’est-à-dire le système dans lequel le programme étant débogé fonctionne. Le CLR est l’heure d’exécution pour le code géré, et l’heure d’exécution Win32 est pour les applications Windows natives. Si la langue que vous créez peut cibler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’un de ces deux temps d’exécution, fournit déjà les moteurs de déboguer nécessaires. Tout ce que vous avez à mettre en œuvre est un évaluateur d’expression.

## <a name="debug-engine-operation"></a>Fonctionnement du moteur Debug
 Les services de surveillance sont implémentés à travers les interfaces DE et peuvent faire en sorte que le paquet de débogé de déboise passe d’un mode opérationnel à l’autre. Pour plus d’informations, voir [modes opérationnels](../../extensibility/debugger/operational-modes.md). Il n’y a généralement qu’une seule mise en œuvre DE par environnement de temps de course.

> [!NOTE]
> Bien qu’il existe des implémentations DE séparées pour Transact-SQL et [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript et [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] partager un seul DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Le débogage permet aux moteurs de déboguer de fonctionner [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de deux façons : soit dans le même processus que la coque, soit dans le même processus que le programme cible étant débogé. Cette dernière forme se produit habituellement lorsque le processus est déboché est en fait un script en cours d’exécution sous un interprète. Le moteur de débogé doit avoir une connaissance intime de l’interprète afin de surveiller le script. Dans ce cas, l’interprète est en fait un runtime; les moteurs de débogé sont pour des implémentations spécifiques de temps d’exécution. En outre, la mise en œuvre d’un seul DE peut être divisée entre les limites du processus et de la machine (par exemple, le débogage à distance).

 Le DE expose [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les interfaces de débogage. Toute communication se fait par l’intermédiaire de COM. Que le DE soit chargé en cours de traitement, hors-processus ou sur un autre ordinateur, il n’affecte pas la communication des composants.

 Le DE fonctionne avec un composant d’évaluateur d’expression pour permettre au DE pour ce temps d’exécution particulier de comprendre la syntaxe des expressions. Le DE travaille également avec un composant de gestionnaire de symbole pour accéder aux informations symboliques de débaillement générées par le compilateur de langue. Pour plus d’informations, voir [Expression evaluator](../../extensibility/debugger/expression-evaluator.md) et [fournisseur de symboles](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Voir aussi
- [Composants Debugger](../../extensibility/debugger/debugger-components.md)
- [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)
- [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)
