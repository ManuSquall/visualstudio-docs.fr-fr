---
title: Émulation de l’utilisation réelle d’un site web pour les tests de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 167dc55e5df18033a9bf16e8aa66e37db9fc6fea
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918336"
---
# <a name="test-mix-models-overview"></a>Vue d’ensemble des modèles de combinaison de tests

Vous utilisez les options de modélisation de charge pour prédire l’utilisation réelle attendue d’un site web ou d’une application dont vous testez la charge. Il est important de le faire, car un test de charge qui n’est pas basé sur un modèle de charge précis peut générer des résultats trompeurs.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Améliorations du modèle de combinaison de tests

À l'aide de l'éditeur de test de charge ou de l'Assistant de modèle de combinaison de tests, vous pouvez spécifier les types suivants de combinaison de tests pour un scénario de test de charge : Pour plus d’informations, consultez [Changement du modèle de combinaison de tests dans un scénario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Vous pouvez spécifier l'une des options de modèle de combinaison de tests suivantes pour votre scénario de test de charge :

- **Sur la base du nombre total de tests :** détermine les tests de performances web ou tests unitaires qui sont exécutés quand un utilisateur virtuel démarre une itération de test. À la fin du test de charge, le nombre de fois où un test particulier exécuté correspond à la distribution de test assignée. Utilisez ce modèle de combinaison de tests lorsque vous basez la combinaison de tests sur les pourcentages de transaction dans un journal IIS ou dans les données de production. Pour plus d’informations, consultez [Pourcentage basé sur les tests démarrés](#BasedOnTestsStarted).

- **Sur la base du nombre d’utilisateurs virtuels :** détermine le pourcentage des utilisateurs virtuels qui vont exécuter un test de performances web ou un test unitaire particulier. À tout point pendant le test de charge, le nombre d'utilisateurs qui exécutent un test particulier correspond d'aussi près que possible à la distribution assignée de la manière la plus fidèle possible. Utilisez ce modèle de combinaison de tests lorsque vous basez la combinaison de tests sur le pourcentage d'utilisateurs qui exécutent un test particulier. Pour plus d’informations, consultez [Pourcentage basé sur les utilisateurs virtuels](#PercentageBasedonVirtualUsers).

- **Sur la base du rythme de l’utilisateur :** au cours du test de charge, chaque test de performances web ou test unitaire est exécuté un nombre spécifique de fois, par utilisateur et par heure. Utilisez ce modèle de combinaison de tests lorsque vous souhaitez que les utilisateurs virtuels exécutent des tests à un certain rythme dans le test de charge. Pour plus d’informations, consultez [Combinaison de tests rythmée](#PacingTestMix).

    > [!TIP]
    > Quand choisir **un pourcentage de combinaison de tests** et quand choisir **un pourcentage basé sur les utilisateurs virtuels** ? La différence entre ces deux choix est importante lorsque certains tests dans la combinaison de tests ont une durée beaucoup plus longue que d'autres. Dans cette situation, vous devrez probablement choisir **un pourcentage basé sur les utilisateurs virtuels**. Ce choix aide à éviter une série de tests au cours de laquelle trop d'utilisateurs risquent d'effectuer des tests de longue durée. Toutefois, si les tests ont tous une durée comparable, vous pouvez sans risque choisir **le pourcentage de combinaison de tests**.

- **Sur la base de l’ordre de tests séquentiel :** chaque utilisateur virtuel exécute les tests de performances web ou les tests unitaires dans l’ordre dans lequel les tests sont définis dans le scénario. L'utilisateur virtuel continue à parcourir les tests dans cet ordre jusqu'à ce que le test de charge soit terminé. Pour plus d’informations, consultez [Ordre Séquentiel](#SequentialOrder).

### <a name="BasedOnTestsStarted"></a> Pourcentage basé sur les tests démarrés

Pour chaque test de la combinaison, vous pouvez spécifier un pourcentage qui détermine sa fréquence de sélection comme prochain test à exécuter. Par exemple, vous pouvez assigner les pourcentages suivants à trois tests :

- TestA (50%)

- TestB (35%)

- TestC (15%)

Lorsque ce paramètre est défini, le prochain test à démarrer dépend des pourcentages assignés. Cette opération est effectuée sans tenir compte du nombre d'utilisateurs virtuels qui exécutent actuellement chacun des tests.

### <a name="PercentageBasedonVirtualUsers"></a> Pourcentage basé sur le nombre d’utilisateurs virtuels
Ce modèle de combinaison de tests détermine le pourcentage d'utilisateurs virtuels qui effectueront un test particulier. Si vous utilisez ce modèle de combinaison de tests, le prochain test à démarrer dépend non seulement des pourcentages assignés, mais aussi du pourcentage d'utilisateurs virtuels qui exécutent actuellement un test particulier. À tout point pendant le test de charge, le nombre d'utilisateurs qui exécutent un test particulier correspond d'aussi près que possible à la distribution assignée.

### <a name="PacingTestMix"></a> Combinaison de tests rythmée

Si vous spécifiez un rythme de combinaison de tests, vous devez définir un taux d'exécution de tests pour chaque utilisateur virtuel et chaque test dans la combinaison. Pour chaque test, ce taux est exprimé sous forme de série de tests par utilisateur virtuel et par heure. Par exemple, vous pouvez assigner le rythme de combinaison de tests suivant aux tests ci-dessous.

- TestA : 4 tests par utilisateur et par heure

- TestB : 2 tests par utilisateur et par heure

- TestC : 0,125 test par utilisateur et par heure

Si vous utilisez le modèle de combinaison de tests rythmée, le moteur d'exécution de test de charge garantit que le taux réel de démarrage des tests sera inférieur ou égal au taux spécifié. Si la durée d'exécution des tests est trop longue pour pouvoir achever le nombre de tests assigné, une erreur est retournée.

Le paramètre **Temps de réflexion entre les itérations de test** ne s’applique pas quand vous utilisez une combinaison de tests rythmée.

#### <a name="apply-distribution-to-pacing-delay"></a>Appliquer une distribution au rythme
La propriété **Appliquer une distribution au rythme** dans un scénario de test de charge peut avoir la valeur True ou False :

- **True** : le scénario applique des délais de distribution statistiques normaux spécifiés par la valeur de la colonne **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests**. Pour plus d’informations, consultez [Modifier des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Supposons que vous ayez comme valeur **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests** du jeu de tests 2 utilisateurs par heure. Si la propriété **Appliquer une distribution au rythme** a la valeur **True**, une distribution statistique classique s’applique au délai d’attente entre les tests. Les tests exécuteront toujours 2 tests par heure, mais l'intervalle entre eux ne sera pas nécessairement de 30 minutes. Le premier test peut être exécuté après 4 minutes et le deuxième test après 45 minutes.

- **False** : les tests seront exécutés à un rythme spécifique que vous avez spécifié avec la valeur de la colonne **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests**. Pour plus d’informations, consultez [Modifier des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Supposons que vous ayez comme valeur **Tests par utilisateur et par heure** dans la boîte de dialogue **Modifier la combinaison de tests** du jeu de tests 2 utilisateurs par heure. Si la propriété **Appliquer une distribution au rythme** a la valeur **False**, vous n’avez pour ainsi dire aucune marge de manœuvre pour exécuter vos tests. Le test s'exécutera toutes les 30 minutes. Cela permet de s'assurer que vous exécutez 2 tests par heure.

  Pour plus d'informations, voir [Procédure : Appliquer une distribution au rythme durant l’utilisation d’un modèle de combinaison de tests dépendant du rythme de l’utilisateur](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="SequentialOrder"></a> Ordre séquentiel
Sélectionner l'option Basé sur l'ordre séquentiel des tests permet à chaque utilisateur virtuel d'exécuter tous les tests du scénario dans l'ordre dans lequel les tests ont été définis.

## <a name="test-iterations-property"></a>Propriété des itérations de tests
Dans les propriétés Paramètres d'exécution, vous pouvez spécifier une valeur pour la propriété des itérations de tests. Cette valeur définit le nombre d'itérations de tests à exécuter dans un test de charge. Une fois que le nombre d'itérations de tests spécifié a été démarré, aucune itération supplémentaire n'a lieu, quels que soient les paramètres définis dans les profils de charge. Une fois que le nombre d'itérations de tests spécifié a été réalisé, le test de charge s'achève. Pour plus d'informations, voir [Procédure : Spécifier le nombre d’itérations de tests dans un paramètre d’exécution](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Tests d'initialisation et de fin
Vous pouvez sélectionner les tests à exécuter au début et à la fin de la session de test de charge de chaque utilisateur virtuel. Pour plus d’informations, consultez [Modifier des modèles de combinaison de texte pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Test d’initialisation**. Ce test est exécuté par chaque utilisateur virtuel avant les différents tests de la combinaison de tests.

- **Test de fin**. Ce test est exécuté après que tous les tests d'un utilisateur virtuel particulier ont été effectués.

  Prenez note des points suivants à propos des tests d'initialisation et de fin :

- Vous pouvez spécifier la durée du test de charge par heure au lieu de la spécifier par nombre d'itérations. Dans ce cas, le test de fin n'est pas exécuté si la durée de la série de tests de charge est dépassée.

- Si le test de fin est un test unitaire ou un test de performances de site web, l'état de l'objet TestContext ou WebTestContext est enregistré lorsque le test d'initialisation s'achève. Il va être utilisé comme contexte initial pour les itérations de tests dans la combinaison de tests.

- La valeur Nouveaux Utilisateurs, telle qu'elle est définie dans la propriété Pourcentage de nouveaux utilisateurs du scénario, exécute systématiquement le test d'initialisation, une itération de tests de la combinaison de tests et le test de fin.

## <a name="see-also"></a>Voir aussi

- [Modifier les modèles de combinaison de tests pour spécifier la probabilité d’exécution d’un test par un utilisateur virtuel](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Modification de la combinaison de tests pour spécifier les tests à inclure dans un scénario de test de charge](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Configurer les paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
- [Changer le modèle de combinaison de tests dans un scénario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)