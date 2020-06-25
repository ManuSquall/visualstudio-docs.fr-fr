---
title: Configurer les outils de conteneur Visual Studio
description: Configurez les outils disponibles dans Visual Studio pour l’utilisation des conteneurs de l’ancrage.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: d2b3e2821e7697ad53b10a7148c22140aa1a07af
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283214"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Comment configurer les outils de conteneur Visual Studio

À l’aide des paramètres de Visual Studio, vous pouvez contrôler certains aspects du fonctionnement de Visual Studio avec les conteneurs de l’ancrage, y compris les paramètres qui affectent l’utilisation des ressources et des performances lors de l’utilisation de conteneurs de l’ancrage.

## <a name="container-tools-settings"></a>Paramètres des outils de conteneur

Dans le menu principal, choisissez **Outils > Options**, puis développez **Outils de conteneur > Paramètres**. Les paramètres des outils de conteneur s’affichent.

::: moniker range="vs-2017"

![Options des outils de conteneur Visual Studio, afficher : extraire automatiquement les images de l’ancrage requis lors du chargement du projet, démarrer automatiquement les conteneurs en arrière-plan, supprimer automatiquement les conteneurs à la fermeture de la solution et ne pas demander l’approbation du certificat SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Paramètres **généraux** des outils de conteneur :

![Options des outils de conteneur Visual Studio, qui indiquent : installer le Bureau de l’ancrage si nécessaire et approuver ASP.NET Core certificat SSL.](./media/configure-container-tools/tools-options-1.png)

Paramètres de **projet** et de **docker compose** des outils de conteneur :

![Options des outils de conteneur Visual Studio, afficher : supprimer les conteneurs sur le projet fermer, extraire les images de l’ancrage requis sur le projet ouvert et exécuter les conteneurs sur le projet ouvert.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Le tableau suivant peut vous aider à déterminer comment définir ces options.

::: moniker range="vs-2017"
| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Extraire automatiquement des images Docker nécessaires lors du chargement du projet | Activé | Docker Compose | Pour améliorer les performances lors du chargement des projets, Visual Studio démarre une opération d’extraction Docker en arrière-plan de sorte que lorsque vous êtes prêt à exécuter votre code, l’image est déjà téléchargée ou en cours de téléchargement. Si vous chargez simplement des projets et parcourez du code, vous pouvez désactiver cette option pour éviter le téléchargement des images conteneur dont vous n’avez pas besoin. |
| Démarrer automatiquement les conteneurs en arrière-plan | Activé | Docker Compose | De nouveau pour améliorer les performances, Visual Studio crée un conteneur avec des montages de volume déjà prêts quand vous créez et exécutez votre conteneur. Si vous voulez contrôler le moment auquel est créé votre conteneur, désactivez cette option. |
| Tuer automatiquement les conteneurs lors de la fermeture de la solution | Activé | Docker Compose | Désactivez cette option si vous voulez que les conteneurs de votre solution continuent à s’exécuter après la fermeture de la solution ou la fermeture de Visual Studio. |
| Ne pas demander l’approbation du certificat SSL localhost | Désactivé | Projets ASP.NET Core 2,1 | Si le certificat SSL localhost n’est pas approuvé, Visual Studio vous invite à le faire chaque fois que vous exécutez votre projet, sauf si cette case est cochée. |
::: moniker-end

::: moniker range=">=vs-2019"

Le tableau suivant décrit les paramètres **généraux** :

| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Installer le Bureau de l’arrimeur si nécessaire | Me demander | Projet unique, Docker Compose | Indiquez si vous souhaitez être invité à indiquer si le Bureau de l’ordinateur de veille n’est pas installé. |
| Approuver ASP.NET Core certificat SSL | Me demander | ASP.NET Core les projets 2. x | Lorsqu’il est défini sur **me demander**, si le certificat SSL localhost n’est pas approuvé, Visual Studio vous invite à chaque fois que vous exécutez votre projet. |

Le tableau suivant décrit les paramètres de projet et de **docker compose** **uniques** :

| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Extraire les images de l’ancrage requis sur le projet ouvert | True | Projet unique, Docker Compose | Pour améliorer les performances lors du chargement des projets, Visual Studio démarre une opération d’extraction Docker en arrière-plan de sorte que lorsque vous êtes prêt à exécuter votre code, l’image est déjà téléchargée ou en cours de téléchargement. Si vous êtes en train de charger des projets et de parcourir le code, vous pouvez définir sur **false** pour éviter de télécharger des images conteneur dont vous n’avez pas besoin. |
| Exécuter les conteneurs sur le projet ouvert | True | Projet unique, Docker Compose | Là encore, pour des performances accrues, Visual Studio crée un conteneur à l’avance afin qu’il soit prêt pour le moment où vous générez et exécutez votre conteneur. Si vous souhaitez contrôler le moment de la création de votre conteneur, affectez la valeur **false**. |
| Arrêter les conteneurs à la fermeture du projet | True | Projet et Docker Compose uniques | Affectez la valeur **false** si vous souhaitez que les conteneurs de votre solution continuent à s’exécuter après la fermeture de la solution ou la fermeture de Visual Studio. |

::: moniker-end
> [!WARNING]
> Si le certificat SSL localhost n’est pas approuvé et que vous activez la case à cocher pour supprimer les invites de confirmation, les requêtes Web HTTPs risquent d’échouer au moment de l’exécution dans votre application ou service. Dans ce cas, décochez la case **Ne pas demander**, exécutez votre projet et confirmez l’approbation à l’invite.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation des conteneurs dans Visual Studio, consultez cette [vue d’ensemble](overview.md).