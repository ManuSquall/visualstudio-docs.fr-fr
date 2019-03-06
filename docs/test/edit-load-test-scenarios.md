---
title: Scénarios de test de charge
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 647548a59c965b6feacb994efa041ecd5b6c6b91
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908802"
---
# <a name="edit-load-test-scenarios"></a>Modifier les scénarios de test de charge

Un *scénario de test de charge* spécifie le modèle de charge, ainsi que la combinaison de tests, de navigateurs et de réseaux. Les scénarios sont importants, car ils vous permettent de configurer des tests pour simuler des charges de travail complexes et réalistes.

Par exemple, vous pouvez tester un site de commerce électronique qui a une vitrine Internet utilisée par des centaines de clients simultanés, connectés par le biais de nombreuses vitesses de connexion et utilisant différents navigateurs. Le même site peut également avoir une fonction d'administration utilisée par les employés internes pour mettre à jour des produits et consulter des statistiques. Ces utilisateurs internes accèdent en général au site à l'aide du même navigateur et d'une connexion de réseau local rapide. Vous souhaiteriez encapsuler les propriétés de ces deux groupes d'utilisateurs différents dans des scénarios différents. Chaque scénario peut contenir un type d'utilisateur virtuel. Dans ce cas, un scénario de test de charge peut être créé pour représenter des clients virtuels et un autre pour représenter les utilisateurs internes virtuels d’un site web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Composants du scénario

Les options et paramètres de configuration initiaux que vous spécifiez quand vous créez un test de charge peuvent être modifiés plus tard dans l’**éditeur de test de charge**. Vous pouvez également ajouter de nouveaux scénarios, paramètres d’exécution et ensembles de compteurs à un test de charge.

![Scénarios de test de charge](../test/media/loadtesteditinscenarios.png)

Les scénarios contiennent les composants suivants :

|Terme|Définition|
|-|-|
|Combinaison de navigateurs|Simule l’accès des utilisateurs virtuels à un site web via divers navigateurs web.|
|Modèle de charge|Spécifie le nombre d’utilisateurs virtuels actifs pendant un test de charge, ainsi que le taux de démarrage des nouveaux utilisateurs. Par exemple : étape, constante et en fonction des objectifs.|
|Modèle de combinaison de tests|Spécifie la probabilité qu'un utilisateur virtuel exécute un test donné dans un scénario de test de charge. Par exemple : 20 % de chance d’exécuter le TestA et 80 % de chance d’exécuter le TestB. Le modèle de combinaison de tests doit refléter les objectifs de votre test pour un scénario particulier.|
|Combinaison de tests|La combinaison de tests représente la sélection des tests de performances web et des tests unitaires contenus dans le scénario, ainsi que la distribution de ces tests.|
|Combinaison de réseaux|Simule l’accès des utilisateurs virtuels à un site web via diverses connexions réseau. La combinaison de réseaux offre des options telles que le réseau local, le modem câble, et ainsi de suite.|

Un scénario comporte plusieurs autres propriétés que vous pouvez modifier à l’aide de l’**éditeur de test de charge**. Pour plus d’informations, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-|-----------------------|
|**Ajouter des pauses d’interaction humaine artificielle dans votre scénario :** Les temps de réflexion permettent de simuler un comportement humain selon lequel les utilisateurs attendent entre des interactions avec un site web. Ils ont lieu entre les demandes dans un test de performances web et entre les itérations de test dans un scénario de test de charge. L'utilisation de temps de réflexion dans un test de charge peut être utile pour la création de simulations de charge plus précises.|-   [Modifier les temps de réflexion pour simuler les retards d’interaction humaine avec un site web](../test/edit-think-times-in-load-test-scenarios.md)|
|**Spécifiez le nombre d’utilisateurs virtuels pour votre scénario :** vous pouvez configurer les propriétés du modèle de charge pour spécifier le mode d’ajustement de la charge utilisateur simulée pendant un test de charge. Vous obtenez trois modèles de charge intégrés : constant, dans l’étape et en fonction des objectifs. Vous choisissez le modèle de charge et ajustez les propriétés aux niveaux appropriés à vos objectifs de test de charge.|-   [Modifier des modèles de charge pour modéliser les activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Configurer la probabilité qu’un utilisateur virtuel exécute un test dans le scénario :** vous pouvez utiliser le la combinaison de tests, qui spécifie la probabilité qu’un utilisateur virtuel exécute un test donné dans un scénario de test de charge. Cela vous permet de simuler la charge de façon plus réaliste. Au lieu d'avoir un seul flux de travail dans vos applications, vous pouvez en avoir plusieurs, ce qui représente une meilleure approximation de la façon dont les utilisateurs finaux interagissent avec vos applications.|-   [Modifier des modèles de combinaison de tests](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Ajouter ou supprimer un test unitaire ou un test de performances web dans un scénario de test de charge :** vous pouvez ajouter ou supprimer un test unitaire ou un test de performances web dans un scénario. Un test de charge contient un ou plusieurs scénarios, chacun contenant un ou plusieurs tests unitaires ou de performances web.|-   [Modifier la combinaison de tests](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Configurer la combinaison de réseaux souhaitée pour votre scénario :** à l’aide de la combinaison de réseaux, vous pouvez simuler la charge réseau avec davantage de réalisme dans un scénario de test de charge. La charge est générée à l'aide d'une combinaison hétérogène de types de réseaux au lieu d'un seul type de réseau. Vous créez une meilleure approximation de la façon dont les utilisateurs finaux interagissent avec vos applications. Le modèle de combinaison de réseaux doit refléter les objectifs de ce scénario.|-   [Spécifier des types de réseau virtuel](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Sélectionner la combinaison de navigateurs web appropriée pour votre scénario :** à l’aide de la combinaison de navigateurs, vous pouvez simuler la charge web avec davantage de réalisme dans un scénario de test de charge. La charge est générée à l'aide d'une combinaison hétérogène de navigateurs au lieu d'un seul navigateur. Vous créez une approximation plus proche des navigateurs qui seront utilisés avec vos applications.|-   [Spécifier des types de navigateurs web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Configurer les paramètres d’itération de test pour votre scénario :** vous pouvez modifier un scénario de test de charge pour configurer des paramètres d’itération de test à l’aide de l’éditeur de test de charge et de la fenêtre Propriétés. Par défaut, un scénario ne comprend pas de limite d'itérations de tests. Vous pouvez aussi configurer le nombre maximal d'itérations du scénario, ainsi que la durée de pause entre deux itérations.|-   [Configurer des itérations de tests pour des scénarios](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Configurer les paramètres de délai pour votre scénario :** à l’aide de l’**éditeur de test de charge** et de la fenêtre **Propriétés**, vous pouvez spécifier un délai avant le démarrage d’un scénario dans un test de charge. Par exemple, vous pouvez utiliser la propriété **Retarder l’heure de début** si vous avez besoin qu’un scénario commence à produire des éléments consommés par un autre scénario. Vous pouvez retarder le scénario d'utilisation pour permettre au scénario de production de remplir certaines données.|-   [Configurer des délais de démarrage des scénarios](../test/configure-scenario-start-delays.md)|
|**Spécifier les ordinateurs distants à utiliser dans un scénario de test de charge :** après avoir créé un test de charge, vous pouvez modifier les propriétés de votre scénario de test de charge pour indiquer les agents de test à inclure. Pour plus d’informations, consultez [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md).|-   [Guide pratique pour spécifier les agents de test à utiliser](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Voir aussi

- [Modifier des tests de charge](../test/edit-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)