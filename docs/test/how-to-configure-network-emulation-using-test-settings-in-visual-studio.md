---
title: Configurer l’émulation réseau à l’aide de paramètres de test
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 032eff41f0e6b6366e5eb56dad591a02ebde4984
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065893"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Procédure : configurer l’émulation réseau à l’aide de paramètres de test dans Visual Studio

Vous pouvez configurer l’adaptateur de données de diagnostic pour tester votre application sous différents environnements réseau à partir de Visual Studio. Vous pouvez également le configurer pour tester une charge réseau artificielle ou un goulot d’étranglement, durant l’exécution des tests.

> [!WARNING]
> Si vous exécutez vos tests sur un vrai réseau d'un type plus lent que le réseau que vous émulez, le test s'exécutera à la vitesse réseau la plus lente. L'émulation peut uniquement ralentir l'environnement réseau, pas l'accélérer.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La procédure suivante décrit comment configurer l'émulation de réseau à partir de l'éditeur de configuration. Ces étapes s’appliquent à l’éditeur de configuration de Microsoft Test Manager et Visual Studio.

> [!NOTE]
> L'adaptateur de diagnostic de données de l'émulation de réseau s'applique uniquement aux paramètres de test Visual Studio. Il n’est pas utilisé pour les paramètres de test dans Microsoft Test Manager.

Un compte qui est doté de privilèges d'administrateur doit être utilisé pour l'émulation de réseau. Si vous avez sélectionné l’émulation réseau pour un rôle local qui exécute des tests manuels, vous devez démarrer Microsoft Test Manager en utilisant des privilèges d’administrateur. Si vous avez sélectionné l’émulation de réseau pour n’importe quel autre rôle, vous devez vérifier que l’agent de test de l’ordinateur correspondant à ce rôle utilise un compte d’utilisateur qui est membre du groupe Administrateurs. Pour plus d’informations sur la façon de configurer le compte de votre agent de test, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Le compte Service réseau, qui est le compte par défaut de l’agent de test, n’est pas membre du groupe Administrateurs.

**Émulation réseau véritable**

Visual Studio utilise une émulation de réseau véritable basée sur un logiciel pour tous les types de tests. Cela inclut des tests de charge. L'émulation de réseau véritable simule les conditions d'un réseau par manipulation directe des paquets réseau. L'émulateur de réseau véritable peut émuler le comportement des réseaux avec et sans fil en utilisant un lien physique fiable, par exemple Ethernet. Les attributs de réseau suivants sont incorporés dans une émulation de réseau véritable :

- Délai aller-retour sur le réseau (latence)

- Bande passante disponible

- Comportement de mise en file d'attente

- Perte de paquets

- Réorganisation des paquets

- Propagations des erreurs

L'émulation de réseau véritable fournit également la flexibilité nécessaire au filtrage des paquets réseau selon les adresses IP ou en fonction des protocoles tels que TCP, UDP et ICMP.

L'émulation de réseau véritable peut être utilisée par les testeurs et les développeurs réseau pour émuler un environnement de test souhaité, évaluer les performances, prévoir l'impact des modifications ou prendre des décisions en matière d'optimisation de technologie. En comparaison des bancs d'essais matériels, l'émulation de réseau véritable est une solution bien plus économique et plus flexible.

## <a name="configure-network-emulation-for-your-test-settings"></a>Configurer l’émulation réseau pour vos paramètres de test

Avant d’effectuer les étapes de cette procédure, vous devez ouvrir les paramètres de test depuis Visual Studio, puis sélectionner la page **Données et diagnostics**.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Pour configurer l'émulation de réseau pour vos paramètres de test

1.  Sélectionnez le rôle à utiliser pour émuler un réseau spécifique.

    > [!NOTE]
    > Vous devez configurer l'adaptateur de l'émulation du réseau uniquement pour le rôle client ou le rôle serveur. Vous ne devez pas utiliser l'adaptateur pour les deux rôles. L'adaptateur émule le bruit de réseau qui affecte la communication entre les deux rôles. Ainsi, vous n'avez pas à utiliser les deux à la fois. Vous devez choisir un rôle client pour l'adaptateur de l'émulation de réseau pour éviter une charge supplémentaire sur le rôle serveur, sauf si cela s'avère nécessaire.

2.  Sélectionnez **Émulation réseau**, puis choisissez **Configurer**.

     La boîte de dialogue permettant de configurer l'émulation de réseau s'affiche.

3.  Choisissez la flèche en regard de **Sélectionner le profil de réseau à utiliser**, puis sélectionnez le type de réseau à émuler quand vous exécutez un test (par exemple **Câble-DSL 768 Ko/s**).

    > [!WARNING]
    > Si vous exécutez vos tests sur un vrai réseau d'un type plus lent que le réseau que vous émulez, le test s'exécutera à la vitesse réseau la plus lente. L'émulation peut uniquement ralentir l'environnement réseau, pas l'accélérer.

4.  Si vous incluez l'adaptateur de données de diagnostic de l'émulation du réseau dans les paramètres de test et que vous prévoyez de l'utiliser sur votre ordinateur local, vous devez également lier le pilote d'émulation des cartes réseau de votre ordinateur. Le pilote d'émulation de réseau est obligatoire pour que l'adaptateur de données de diagnostic de l'émulation du réseau fonctionne. Le pilote d'émulation de réseau est installé et lié à votre adaptateur de deux manières :

    -   **Pilote d’émulation réseau installé avec Microsoft Visual Studio Test Agent :** Microsoft Visual Studio Test Agent peut être utilisé sur des machines distantes et des machines locales. Lorsque vous installez Visual Studio Test Agent, le processus d’installation inclut une étape de configuration qui lie le pilote d’émulation de réseau à votre carte réseau. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

    -   **Pilote d’émulation réseau installé avec Microsoft Visual Studio Test Professional :** quand vous utilisez l’émulation réseau pour la première fois, vous êtes invité à lier le pilote d’émulation réseau à une carte réseau.

    > [!TIP]
    > Vous pouvez également installer le pilote d’émulation réseau à partir de la ligne de commande sur votre machine locale sans installer Visual Studio Test Agent, à l’aide de la commande suivante : **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Voir aussi

- [Collecter des informations de diagnostic à l’aide des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)
- [Exécuter des tests manuels (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts)