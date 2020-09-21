---
title: Configurer des agents de test/contrôleurs de test pour les tests de charge
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe6811f4deaa5958b050a8f93f74e48e2dc73f38
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809287"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Vue d’ensemble des agents de test et des contrôleurs de test pour l’exécution de tests de charge

Visual Studio peut utiliser des ordinateurs physiques ou des machines virtuelles pour générer une charge simulée pour votre application. Ces ordinateurs doivent être configurés comme un contrôleur de test unique, et un ou plusieurs agents de test. Vous pouvez utiliser le contrôleur de test et les agents de test pour générer une charge supérieure à celle qu'un seul ordinateur peut générer à lui seul.

> [!NOTE]
> Vous pouvez également utiliser le test de charge cloud pour fournir des machines virtuelles qui génèrent la charge de nombreux utilisateurs accédant simultanément à votre site web. Toutefois, l’utilisation du contrôleur de test/de l’installation de l’agent de test sur des ordinateurs virtuels hébergés dans le Cloud n’est pas prise en charge. Découvrez plus d’informations sur les tests de charge basés sur le cloud dans [Exécuter des tests de charge avec Azure Test Plans](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architecture de la simulation de charge

L'architecture de la simulation de charge se compose d'un client Visual Studio, d'un contrôleur de test et d'agents de test.

- Le client est utilisé pour développer les tests, exécuter les tests et en afficher les résultats.

- Le contrôleur de test est utilisé pour administrer les agents de test et pour collecter les résultats des tests.

- Les agents de test sont utilisés pour exécuter les tests et pour collecter des données, y compris les informations système et les données de profilage ASP.NET définies dans les paramètres de test.

Cette architecture offre les avantages suivants :

- La possibilité de faire évoluer la génération de charge en ajoutant des agents de test supplémentaires à un contrôleur de test.

- Une flexibilité pour l'installation du logiciel du client, du contrôleur de test et des agents de test sur le même ordinateur ou sur différents ordinateurs. Exemple :

   **Configuration locale :**

  - Ordinateur1 : Visual Studio, contrôleur, agent.

    ![Ordinateur local utilisant le contrôleur et l'agent](./media/load-test-configa.png)

    **Configuration à distance classique :**

  - Ordinateur1 et Ordinateur2 : Visual Studio (plusieurs testeurs peuvent utiliser le même contrôleur).

  - Ordinateur3 : contrôleur (sur lequel des agents peuvent également être installés).

  - Ordinateur4-n : agent ou agents tous associés au contrôleur sur Ordinateur3.

    ![Ordinateurs locaux utilisant le contrôleur et les agents](./media/load-test-configb.png)

Même si un contrôleur de test gère en général plusieurs agents de test, un agent ne peut être associé qu'à un seul contrôleur. Chaque agent de test peut être partagé par une équipe de développeurs. Cette architecture permet d'augmenter facilement le nombre d'agents de test, ce qui génère des charges plus importantes.

## <a name="test-agent-and-test-controller-interaction"></a>Interaction entre un agent de test et un contrôleur de test

Le contrôleur de test gère un ensemble d'agents de test pour exécuter des tests. Le contrôleur de test communique avec les agents de test pour démarrer les tests, arrêter les tests, suivre l'état des agents de test et collecter les résultats des tests.

### <a name="test-controller"></a>Contrôleur de test

Le contrôleur de test fournit une architecture générale pour l'exécution de tests et comprend des fonctionnalités spécifiques pour l'exécution de tests de charge. Le contrôleur de test envoie le test de charge à tous les agents de test et attend qu’ils aient initialisé le test. Quand tous les agents de test sont prêts, le contrôleur de test envoie un message aux agents de test pour qu'ils démarrent le test.

### <a name="test-agent"></a>Agent de test

L'agent de test s'exécute en tant que service qui écoute les demandes de démarrage d'un nouveau test envoyées par le contrôleur de test. Quand l’agent de test reçoit une demande, le service de l’agent de test démarre un processus sur lequel les tests peuvent être exécutés. Chaque agent de test exécute le même test de charge.

Une pondération est affectée par l’administrateur aux agents de test. La charge est distribuée en fonction de la pondération d’un agent de test. Par exemple, si l'agent de test 1 a une pondération de 30, que l'agent de test 2 a une pondération de 70 et que la charge est définie à 1 000 utilisateurs, l'agent de test 1 simule 300 utilisateurs virtuels tandis que l'agent de test 2 en simule 700. Consultez [Gérer les contrôleurs de test et les agents de test avec Visual Studio](../test/manage-test-controllers-and-test-agents.md).

L'agent de test prend un ensemble de tests et un ensemble de paramètres de simulation comme entrées. Un concept essentiel est que les tests sont indépendants de l'ordinateur sur lequel ils sont exécutés.

## <a name="test-controller-and-test-agent-connection-points"></a>Points de connexion d’un contrôleur de test et d’un agent de test

L'illustration suivante montre les points de connexion entre le contrôleur de test, l'agent de test et le client. Elle décrit les ports utilisés pour les connexions entrantes et sortantes ainsi que les restrictions de sécurité sur ces ports.

![Ports et sécurité du contrôleur de test et de l’agent de test](./media/test-controller-agent-firewall.png)

Pour plus d’informations, consultez [Configurer les ports pour les contrôleurs de test et les agents de test](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informations d’installation du contrôleur et des agents de test

Pour des informations importantes sur les spécifications matérielles et logicielles requises pour les contrôleurs de test et les agents de test, sur les procédures pour les installer et sur la configuration de votre environnement pour des performances optimales, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Utiliser le contrôleur de test et l’agent de test avec des tests unitaires

Après avoir installé un contrôleur de test et un ou plusieurs agents, vous pouvez spécifier s'il faut utiliser une exécution distante avec le contrôleur de test dans les paramètres de test pour vos tests de charge. En outre, vous pouvez spécifier les adaptateurs de données et de diagnostic à utiliser avec le rôle associé aux agents dans les paramètres de test.

## <a name="see-also"></a>Voir aussi

- [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md)
