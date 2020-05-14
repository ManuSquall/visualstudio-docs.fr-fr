---
title: 'Comment : Exécuter l’analyse de code manuellement pour le code géré'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431382"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Comment : Exécuter l’analyse de code manuellement pour le code géré (nécessite visual Studio 2019 version 16.5 ou plus tard)
Par défaut, les analyseurs de code .NET Compiler Platform ("Roslyn") analysent votre code de base visuel ou C ou Visual comme vous tapez en effectuant des analyses en direct, ainsi que pendant la construction. Par conséquent, vous n’auriez normalement pas besoin de déclencher manuellement l’analyse de code. Cependant, il existe certains scénarios où vous pouvez déclencher manuellement l’analyse du code:

- Par défaut, l’analyse de code en direct exécute les analyseurs uniquement pour les fichiers ouverts dans Visual Studio. Toutefois, vous pouvez être intéressé à consulter les avertissements d’analyse de code pour tous les fichiers d’un projet ou d’une solution spécifique. Si c’est le cas, vous souhaitez déclencher l’analyse de code une fois sur un projet ou une solution. Alternativement, vous pouvez activer l’analyse continue de code en direct pour exécuter sur la solution entière. Pour plus d’informations, voir [Comment configurer la portée d’analyse de code en direct pour le code géré](./configure-live-code-analysis-scope-managed-code.md).
- Vous pouvez préférer le flux de travail d’exécution d’exécution d’analyse de code à la demande à l’analyse en direct continue ou à l’analyse du temps de construction. Si c’est le cas, vous pouvez désactiver l’exécution de l’analyseur pendant l’analyse en direct et/ou la construction. Pour plus d’informations sur l’analyse invalidante, voir [Comment désactiver l’analyse du code source](disable-code-analysis.md). Ensuite, vous souhaitez déclencher manuellement l’analyse de code une fois sur un projet ou une solution. 

### <a name="run-code-analysis-manually"></a>Exécuter l’analyse du code manuellement

1. Dans **Solution Explorer**, cliquez sur le projet.

2. Sur le menu **Analyze,** cliquez sur **l’analyse du code d’exécution sur** *le nom du projet*.

L’analyse du code commencera à s’exécuter en arrière-plan. Vous devriez voir le message **Analyse de code de fonctionnement pour \<le projet>...** dans la barre de statut Visual Studio vers le coin inférieur gauche. Une fois l’analyse de code terminée, le message d’état sera modifié pour **l’analyse \<de code effectuée pour le projet>**. La liste d’erreurs se rafraîchira bientôt avec tous les diagnostics d’analyse de code.
