---
title: Comment exécuter l’analyse du code manuellement pour le code managé
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1077e2cdae790fe8a7b7309b1e6427cd3ef81b48
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800162"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Comment : exécuter l’analyse du code manuellement pour le code managé (nécessite Visual Studio 2019 version 16,5 ou ultérieure)
Par défaut, les analyseurs de code .NET Compiler Platform (« Roslyn ») analysent votre code C# ou Visual Basic au fur et à mesure que vous tapez en réalisant une analyse en temps réel, ainsi que pendant la génération. Par conséquent, vous n’avez normalement pas besoin de déclencher manuellement l’analyse du code. Toutefois, dans certains scénarios, vous pouvez être amené à déclencher manuellement l’analyse du code :

- Par défaut, l’analyse du code en direct exécute des analyseurs uniquement pour les fichiers ouverts dans Visual Studio. Toutefois, vous souhaiterez peut-être afficher des avertissements d’analyse du code pour tous les fichiers d’un projet ou d’une solution spécifique. Si c’est le cas, vous pouvez déclencher l’analyse du code une seule fois sur un projet ou une solution. Vous pouvez également activer l’analyse de code en direct en continu pour l’exécuter sur la totalité de la solution. Pour plus d’informations, consultez [Comment : configurer l’étendue de l’analyse du code en temps réel pour le code managé](./configure-live-code-analysis-scope-managed-code.md).
- Vous préférerez peut-être un flux de travail d’exécution de l’analyse du code à la demande sur une analyse en temps réel ou une analyse de la génération. Dans ce cas, vous pouvez désactiver l’exécution de l’analyseur lors de l’analyse et/ou de la génération en temps réel. Pour plus d’informations sur la désactivation de l’analyse, consultez [Comment désactiver l’analyse du code source](disable-code-analysis.md). Ensuite, vous pouvez déclencher manuellement l’analyse du code sur un projet ou une solution. 

### <a name="run-code-analysis-manually"></a>Exécuter l’analyse du code manuellement

1. Dans **Explorateur de solutions**, choisissez le projet.

2. Dans le menu **analyser** , sélectionnez **exécuter l’analyse du code sur le nom du** *projet*.

L’analyse du code commence à s’exécuter en arrière-plan. Vous devez voir le message **exécution de l’analyse du code pour \<project> ...** dans la barre d’état de Visual Studio vers l’angle inférieur gauche. Une fois l’analyse du code terminée, le message d’état passe à l' **analyse \<project> du code terminée pour **. La liste d’erreurs sera bientôt actualisée avec tous les diagnostics d’analyse du code.
