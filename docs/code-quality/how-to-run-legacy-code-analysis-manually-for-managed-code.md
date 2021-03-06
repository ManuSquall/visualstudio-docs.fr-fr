---
title: Exécuter manuellement l’analyse du code hérité (.NET)
description: Découvrez comment détecter des erreurs possibles dans le code source. Consultez Comment exécuter l’analyse du code hérité manuellement sur du code managé dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f214ac47ad3d831432b91652c5bbe3249ce5f1c5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223483"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Comment : exécuter manuellement l’analyse du code hérité pour le code managé

L’outil d’analyse du code vous fournit des informations sur les erreurs possibles dans votre code source. Vous pouvez exécuter l’analyse du code automatiquement avec chaque génération d’un projet de code, et vous pouvez également exécuter l’analyse du code manuellement. Les règles qui sont vérifiées lors de l’exécution de l’analyse du code sont spécifiées dans la page analyse du code des pages de propriétés du projet. Pour plus d’informations, consultez [Comment : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Pour exécuter l’analyse du code manuellement

1. Si vous utilisez Visual Studio 2019 version 16,5 ou ultérieure, exécutez la commande suivante sur l’invite de commandes avant de démarrer Visual Studio :

```
setx EnableLegacyCodeAnalysis true
```

2. Dans **Explorateur de solutions**, cliquez sur le projet.

3. Dans le menu **analyser** , cliquez sur **exécuter l’analyse du code sur** le nom du *projet*.
