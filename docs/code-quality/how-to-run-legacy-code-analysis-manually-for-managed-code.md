---
title: 'Comment : Exécuter l’analyse de code héritée manuellement pour le code géré'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432230"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Comment : Exécuter l’analyse de code héritée manuellement pour le code géré
L’outil d’analyse de code vous fournit des informations sur les défauts possibles dans votre code source. Vous pouvez exécuter l’analyse de code automatiquement avec chaque version d’un projet de code, et vous pouvez également exécuter l’analyse de code manuellement. Les règles qui sont vérifiées lors de l’analyse du code sont spécifiées sur la page d’analyse de code des pages de propriété du projet. Pour plus d’informations, voir [Comment configurer l’analyse de code pour un projet de code géré](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Pour exécuter l’analyse de code manuellement

1. Si vous êtes sur Visual Studio 2019 version 16.5 ou plus tard, exécutez la commande suivante sur la commande prompte avant de commencer Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. Dans **Solution Explorer**, cliquez sur le projet.

3. Sur le menu **Analyze,** cliquez sur **l’analyse du code d’exécution sur** *le nom du projet*.

