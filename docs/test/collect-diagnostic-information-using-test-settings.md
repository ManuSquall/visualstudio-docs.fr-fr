---
title: Collecter des informations de diagnostic avec des paramètres de test
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bf82ee72d4398095f25de2493c28c5155456b55
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588861"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Collecter des informations de diagnostic avec des paramètres de test

Vous pouvez utiliser des *Paramètres de test* dans Visual Studio pour collecter des données supplémentaires quand vous exécutez vos tests. Par exemple, vous pouvez effectuer un enregistrement vidéo quand vous exécutez votre test. Il existe des adaptateurs de données de diagnostic pour :

- Collecter chaque étape de l'action d'interface utilisateur au format texte

- Enregistrer chaque action d'interface utilisateur pour la lire

- Collecter les informations système

- Collecter les données du journal des événements

- Collecter des données IntelliTrace pour aider à isoler les bogues non reproductibles

Les adaptateurs de données de diagnostic peuvent également être utilisés pour modifier le comportement d'un ordinateur de test. Par exemple, avec un paramètre de test dans Visual Studio, vous pouvez émuler plusieurs goulots d'étranglement de la topologie du réseau pour évaluer les performances de l'application de votre équipe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Utiliser des paramètres de test avec Visual Studio

Pour exécuter vos tests unitaires, vos tests codés de l'interface utilisateur, vos tests de performances Web ou de charge à l'aide de Visual Studio, vous pouvez ajouter, configurer et sélectionner les paramètres de test à utiliser lorsque vous exécutez vos tests. Pour exécuter vos tests, collecter des données ou modifier un ordinateur de test à distance, vous devez spécifier un contrôleur de test dans vos paramètres de test. Le contrôleur de test a des agents pouvant être utilisés pour chaque rôle dans vos paramètres de test.

## <a name="diagnostic-data-adapter-details"></a>Détails des adaptateurs de données de diagnostic

Le tableau suivant répertorie les différentes façons de configurer les adaptateurs de données de diagnostic à utiliser avec les rôles d'ordinateurs locaux ou distants.

|Adaptateur de données de diagnostic utilisé dans les paramètres de test|Tests manuels sur un ordinateur local|Tests automatisés|Tests manuels : collection de données à l'aide d'un ensemble de rôles et d'un environnement|Remarques|
|-|-|-|-|-|
|**Proxy client ASP.NET pour l’impact de test et IntelliTrace :** ce proxy permet de collecter des informations sur les appels HTTP d’un client à un serveur web pour les adaptateurs de données de diagnostic d’impact de test et IntelliTrace.|Oui|Oui|Oui|-   Utilisez ceci seulement quand les adaptateurs de données de diagnostic IntelliTrace ou d’impact de test sont sélectionnés pour un rôle client.|
|**Profileur ASP.NET :** vous pouvez créer un paramètre de test incluant le profilage ASP.NET, qui collecte des données de performances relatives aux applications web ASP.NET.|Non|Oui (consultez les remarques)|Non|-   Cet adaptateur de données de diagnostic est pris en charge seulement lors de l’exécution de tests de charge à partir de Visual Studio.|
|**Couverture du code :** vous pouvez créer un paramètre de test comprenant des informations de couverture du code, qui sont utilisées pour évaluer quelle proportion de votre code est couverte par les tests.|Non|Oui (consultez les remarques)|Non|-   Vous pouvez utiliser la couverture du code seulement quand vous exécutez un test automatisé à partir de Visual Studio ou *mstest.exe*, et seulement depuis l’ordinateur qui exécute le test. La collecte distante n'est pas prise en charge.<br />-   La collecte des données de couverture du code ne fonctionne pas si le paramètre de test est également configuré pour collecter des informations IntelliTrace. **Remarque :** Cet adaptateur de données de diagnostic s’applique seulement aux paramètres de test Visual Studio. Il n’est pas utilisé pour les paramètres de test dans Microsoft Test Manager. En outre, cet adaptateur est compatible avec les projets de test Visual Studio 2010. **Remarque :** Pour des raisons de compatibilité, la couverture du code s’applique quand les tests automatisés sont exécutés à partir de Microsoft Test Manager ou sur un agent de test distant depuis Visual Studio en utilisant l’ancienne version de MSTest Runner.|
|**Journal des événements :** vous pouvez configurer un paramètre de test pour inclure la collecte des journaux des événements, qui est intégrée aux résultats des tests.|Oui|Oui|Oui||
|**IntelliTrace :** vous pouvez configurer l’adaptateur de données de diagnostic pour *IntelliTrace* afin de collecter des informations de trace de diagnostic spécifiques pour isoler des bogues qui sont difficiles à reproduire. Cela génère un fichier IntelliTrace qui contient ces informations. Fichier IntelliTrace doté d’une extension *.iTrace*. Lorsqu'un test échoue, vous pouvez créer un bogue. Le fichier IntelliTrace enregistré avec les résultats des tests est automatiquement lié à ce bogue. Les données collectées dans le fichier IntelliTrace augmentent l'efficacité du débogage en réduisant le temps nécessaire à la reproduction et au diagnostic d'une erreur dans le code. De ce fichier IntelliTrace, la session locale peut être simulée sur un autre ordinateur. Cela réduit le risque d'un bogue non reproductible.|Oui|Oui|Oui|-   Si vous activez la collecte des données IntelliTrace, la collecte des données de couverture du code ne fonctionne pas.<br />-   Si vous utilisez IntelliTrace pour un rôle de client web, vous devez également sélectionner le proxy client ASP.NET pour l’adaptateur de données de diagnostic d’impact de test et IntelliTrace.<br />-   Seules les versions suivantes d’IIS sont prises en charge : IIS 7.0, IIS 7.5 et IIS 8.0.|
|**Émulation de réseau :** vous pouvez spécifier que vous voulez appliquer une charge réseau artificielle à votre test en utilisant un paramètre de test. L'émulation de réseau affecte les communications établies vers et depuis l'ordinateur en émulant une vitesse de connexion réseau particulière (par exemple, une connexion d'accès à distance). |Non|Oui (consultez les remarques)|Non|Vous pouvez utiliser l'adaptateur de données de diagnostic de l'émulation du réseau pour un client ou un rôle serveur. Il n'est pas nécessaire d'utiliser l'adaptateur sur ces deux rôles pour que ces derniers communiquent. **Remarque :** Cet adaptateur de données de diagnostic s’applique seulement aux paramètres de test Visual Studio. Il n’est pas utilisé pour les paramètres de test dans Microsoft Test Manager. **Remarque :** L’émulation de réseau ne peut pas être utilisée pour augmenter la vitesse de connexion réseau. **Avertissement :** Si vous incluez l’adaptateur de données de diagnostic de l’émulation de réseau dans les paramètres de test et que vous prévoyez de l’utiliser sur votre ordinateur local, vous devez également lier le pilote d’émulation réseau à une des cartes réseau de votre ordinateur. Le pilote d'émulation de réseau est obligatoire pour que l'adaptateur de données de diagnostic de l'émulation du réseau fonctionne. Le pilote d'émulation de réseau est installé et lié à votre adaptateur de deux manières : <ul><li>**Pilote d’émulation réseau installé avec Microsoft Visual Studio Test Agent :** Visual Studio Test Agent peut être utilisé sur des ordinateurs distants comme sur des ordinateurs locaux. Lorsque vous installez Visual Studio Test Agent, le processus d'installation inclut une étape de configuration qui lie le pilote d'émulation de réseau à votre carte réseau. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).</li><li>**Pilote d’émulation réseau installé avec Microsoft Visual Studio Test Professional :** quand vous utilisez l’émulation réseau pour la première fois, vous êtes invité à lier le pilote d’émulation réseau à une carte réseau.</li></ul> Vous pouvez également installer le pilote d’émulation réseau à partir de la ligne de commande sur votre ordinateur local sans installer Visual Studio test agent à l’aide de la commande suivante : **VSTESTCONFIG NETWORKEMULATION/install** **Warning :** l’adaptateur d’émulation de réseau est ignoré par les tests de charge. Les tests de charge utilisent plutôt les paramètres spécifiés dans la combinaison de réseaux du scénario de test de charge.|
|**Informations système :** un paramètre de test peut être configuré pour inclure les informations système relatives à l’ordinateur sur lequel le test est exécuté.|Oui|Oui|Oui||
|**Impact de test :** vous pouvez collecter des informations sur les méthodes de votre code d’application utilisées lors de l’exécution d’un cas de test. Associées aux modifications apportées au code d'application par les développeurs, ces informations peuvent servir à déterminer les tests impactés par ces modifications.|Oui|Oui|Oui|-   Si vous collectez des données d’impact de test pour un rôle de client web, vous devez également sélectionner le proxy client ASP.NET pour l’adaptateur de données de diagnostic d’impact de test et IntelliTrace.<br />-   Seules les versions suivantes d’IIS sont prises en charge : IIS 7.0, IIS 7.5 et IIS 8.0.|
|**Enregistreur vidéo :** vous pouvez créer un enregistrement vidéo de votre session quand vous exécutez un test. La vidéo peut aider d'autres membres de l'équipe à isoler les problèmes liés aux applications qui sont difficiles à reproduire.|Oui|Oui (consultez les remarques)|Oui|-   Si vous permettez au logiciel d’agent de test de s’exécuter en tant que processus et non pas en tant que service, vous pouvez créer un enregistrement vidéo lors de l’exécution de tests automatisés.|
