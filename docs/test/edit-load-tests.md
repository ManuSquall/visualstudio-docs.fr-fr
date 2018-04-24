---
title: Exécuter des tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6e79dd964593e79c69ec6ec8ab44f10ff4c9ca99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-tests"></a>Modifier des tests de charge

Les tests de charge exécutent des tests de performances web ou des tests unitaires pour simuler l’accès simultané de plusieurs utilisateurs à un serveur. Un test de charge vous donne accès aux données de performance et de contrainte d'une application. Un test de charge peut être configuré pour émuler diverses conditions de charge telles que les charges utilisateur et les types de réseau.

> [!NOTE]
> Les tests de charge sont disponibles seulement dans l’édition Enterprise de Visual Studio 2017.

Un test de charge est défini par des *scénarios*, des *ensembles de compteurs* et des *paramètres d’exécution*. L’illustration suivante explique les différences entre les [scénarios](../test/edit-load-test-scenarios.md), les [ensembles de compteurs](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) et les [paramètres d’exécution](../test/load-test-run-settings-properties.md) :

![Architecture du test de charge](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Modifier les paramètres des scénarios de test de charge

Un scénario est utilisé pour modéliser la manière dont un groupe d’utilisateurs interagit avec une application serveur. Un scénario se compose d’un modèle de charge, d’un modèle de combinaison de tests, d’une combinaison de tests, d’une combinaison de navigateurs et d’une combinaison de réseaux. Un test de charge peut avoir plusieurs scénarios et un scénario peut contenir des tests de performances de site Web et des tests unitaires. En groupant des paramètres semblables, un scénario vous permet de grouper et d'exécuter ensemble des tests de nature semblable.

Pour plus d’informations, consultez [Modification de scénarios de test de charge](../test/edit-load-test-scenarios.md) et [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Configurer et gérer des ensembles de compteurs de performances

Les tests de charge fournissent des ensembles de compteurs nommés, organisés par technologie, qui sont utiles lorsque vous analysez des données de compteur de performance. Les ensembles de compteurs incluent Test de charge, IIS, ASP.NET et SQL. Quand vous créez un test de charge avec l’Assistant Nouveau test de charge, un ensemble initial de compteurs prédéfinis et importants est configuré pour les ordinateurs à inclure dans le test de charge. Vous gérez vos compteurs dans l'éditeur de test de charge.

Pour plus d’informations, consultez [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Configurer et gérer les paramètres d’exécution des tests de charge

Les paramètres d’exécution sont des propriétés qui influencent la façon dont un test de charge s’exécute. Les paramètres d'exécution sont classés par catégories dans la fenêtre Propriétés.

Pour plus d’informations, consultez [Configuration des paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md) et [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Voir aussi

- [Analyser les résultats des tests de charge](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyse des violations des règles de seuil](../test/analyze-threshold-rule-violations-in-load-tests.md)