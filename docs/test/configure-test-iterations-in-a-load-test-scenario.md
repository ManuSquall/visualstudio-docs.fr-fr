---
title: Configuration des itérations de tests pour un test de charge
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ae0f75ac19f858cba9de1e2d75d4ef5529da1d75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665159"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Configurer les itérations de tests dans un scénario de test de charge

Pour configurer les paramètres d’itération de test, modifiez un scénario de test de charge en utilisant l’éditeur de test de charge et la fenêtre **Propriétés**. Par défaut, un scénario de test de charge est configuré sans spécifier d'itérations de test maximum. Vous avez la possibilité de configurer le nombre maximum d'itérations dans le scénario et la durée de pause entre deux itérations.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Spécifier le nombre maximal d’itérations de tests pour un scénario

Vous pouvez spécifier le nombre maximal d’exécutions de vos tests pour un scénario en utilisant l’éditeur de test de charge afin de changer la propriété **Nombre maximal d’itérations de test** dans la fenêtre **Propriétés**.

La propriété **Nombre maximal d’itérations de test** contrôle le nombre maximal d’itérations de tests à exécuter pour le scénario. Comme pour la propriété **Itérations de tests** dans les paramètres d’exécution de test de charge, il s’agit de la valeur maximale relative à tous les utilisateurs sur tous les agents, et non d’un paramètre spécifique à chaque utilisateur.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

Pour une combinaison de tests basée sur un ordre séquentiel, une itération est une opération qui inclut tous les tests de la combinaison. Pour toutes les autres combinaisons de tests, chaque exécution de test compte comme une itération. Pour plus d’informations, consultez [À propos du contrôle de combinaison](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Si le test de charge est basé sur la durée, et si cette dernière expire avant la fin du nombre d'itérations, le test s'arrête. Si le test est basé sur des itérations, et si ces dernières sont effectuées avant les itérations du scénario, le test s'arrête. La durée est configurée à l’aide de la propriété **Durée d’exécution** dans la fenêtre **Propriétés**, en association à un paramètre d’exécution dans un test de charge.

Lorsque le nombre d'itérations du scénario est atteint, le scénario cesse de s'exécuter, mais tous les autres scénarios actifs continuent de s'exécuter.

> [!NOTE]
> La propriété **Unique** est une propriété connexe d’une source de données de test web, qui parcourt les données de manière séquentielle, ligne par ligne, mais une seule fois pour chaque enregistrement. Pour plus d’informations, consultez [Ajouter une source de données à un test de performances web](../test/add-a-data-source-to-a-web-performance-test.md).

La propriété **Nombre maximal d’itérations de test** est utile pour diverses situations. Certains testeurs de charge privilégient les tests basés sur l'itération tandis que d'autres testeurs de charge privilégient les tests basés sur la durée.

![Spécification des itérations de test dans un scénario](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Pour spécifier le nombre maximal d'itérations de test

1. Ouvrez un test de charge.

2. L'Éditeur de test de charge s'affiche. L'arborescence du test de charge s'affiche.

3. Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario pour lequel vous souhaitez spécifier le nombre maximal d’itérations de tests.

4. Dans le menu **Affichage**, sélectionnez la fenêtre **Propriétés**.

     Les catégories et les propriétés du scénario s’affichent dans la fenêtre **Propriétés**.

5. Dans la zone de texte de la propriété **Nombre maximal d’itérations de test**, tapez une valeur qui indique le nombre maximal de tests à exécuter pour le scénario quand le test de charge est exécuté.

    > [!NOTE]
    > L’utilisation de la valeur 0 pour la propriété **Nombre maximal d’itérations de test** indique l’absence d’un nombre maximal d’itérations.

6. Après avoir fini de changer la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Nombre maximal d’itérations de test**.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Spécifier des temps de réflexion entre les itérations de test d’un scénario

La propriété **Temps de réflexion entre les itérations de tests** est définie dans la fenêtre **Propriétés** pendant la modification des propriétés du scénario de test de charge dans l’éditeur de test de charge.

La propriété **Temps de réflexion entre les itérations de tests** est utilisée pour spécifier la durée en secondes à l’issue de laquelle l’itération de test démarre.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Pour spécifier le temps de réflexion entre les itérations de test

1. Ouvrez un test de charge.

     **L’Éditeur de test de charge** s’affiche. L'arborescence du test de charge s'affiche.

2. Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario dont vous souhaitez spécifier le temps de réflexion.

3. Dans le menu **Affichage**, sélectionnez la fenêtre **Propriétés**.

     Les catégories et les propriétés du scénario sont affichées dans la fenêtre **Propriétés**.

4. Pour la valeur de la propriété **Temps de réflexion entre les itérations de tests**, indiquez un nombre qui représente le délai d’attente en secondes avant le démarrage de l’itération de test suivante.

5. Après avoir fini de changer la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Temps de réflexion entre les itérations de tests**.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Configurer les agents de test et les contrôleurs de test pour les tests de charge](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
- [Modifier les temps de réflexion pour simuler les retards d’interaction humaine avec un site web](../test/edit-think-times-in-load-test-scenarios.md)