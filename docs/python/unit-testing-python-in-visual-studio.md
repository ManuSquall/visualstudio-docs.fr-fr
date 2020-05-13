---
title: Test unitaire de code Python
description: La configuration des tests unitaires pour le code Python dans Visual Studio tire pleinement parti des fonctionnalités de l’Explorateur de tests pour la découverte, l’exécution et le débogage de tests.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09c67ace9db36cb8ee3d94296d339b62849e3c94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71254196"
---
# <a name="set-up-unit-testing-for-python-code"></a>Configurer des tests unitaires pour le code Python

Les tests unitaires sont des éléments de code qui permettent de tester d’autres unités de code dans une application, généralement des fonctions isolées, des classes, etc. Quand une application réussit tous ses tests unitaires, vous avez au moins la garantie que ses fonctionnalités secondaires sont correctes.

Python utilise largement les tests unitaires pour valider des scénarios lors de la conception d’un programme. La prise en charge de Python dans Visual Studio inclut la découverte, l’exécution et le débogage de tests unitaires dans le cadre de votre processus de développement, sans qu’il soit nécessaire d’exécuter les tests séparément.

Cet article fournit une brève description des fonctionnalités de tests unitaires contenues dans Visual Studio avec Python. Pour plus d’informations sur les tests unitaires en général, consultez la page [Tests unitaires sur votre code](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end