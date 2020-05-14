---
title: Configurer Visual Studio Container Tools
description: Configurez les outils disponibles dans Visual Studio pour travailler avec des conteneurs Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188771"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Comment configurer Visual Studio Container Tools

En utilisant les paramètres Visual Studio, vous pouvez contrôler certains aspects de la façon dont Visual Studio fonctionne avec des conteneurs Docker, y compris les paramètres qui affectent les performances et l’utilisation des ressources lorsque vous travaillez avec des conteneurs Docker.

## <a name="container-tools-settings"></a>Paramètres d’outils de conteneurs

Dans le menu principal, choisissez **Outils > Options**, puis développez **Outils de conteneur > Paramètres**. Les paramètres des outils de conteneur s’affichent.

::: moniker range="vs-2017"

![Visual Studio Container Tools options, montrant: Tirer automatiquement les images Docker nécessaires sur la charge du projet, démarrer automatiquement les conteneurs en arrière-plan, tuer automatiquement les conteneurs sur la solution fermer, et ne pas inciter à faire confiance certificat SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Paramètres **généraux** des outils de conteneurs :

![Visual Studio Container Tools options, montrant: Installer Docker Desktop si nécessaire, et Trust ASP.NET certificat Core SSL.](./media/configure-container-tools/tools-options-1.png)

Paramètres De Container Tools **Single Project** et **Docker Compose** :

![Visual Studio Container Tools options, montrant: Tuer les conteneurs sur le projet à proximité, Tirer les images Docker requis sur le projet ouvert, et exécuter des conteneurs sur le projet ouvert.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Le tableau suivant peut vous aider à déterminer comment définir ces options.

::: moniker range="vs-2017"
| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Extraire automatiquement des images Docker nécessaires lors du chargement du projet | Il en va | Docker Compose | Pour améliorer les performances lors du chargement des projets, Visual Studio démarre une opération d’extraction Docker en arrière-plan de sorte que lorsque vous êtes prêt à exécuter votre code, l’image est déjà téléchargée ou en cours de téléchargement. Si vous chargez simplement des projets et parcourez du code, vous pouvez désactiver cette option pour éviter le téléchargement des images conteneur dont vous n’avez pas besoin. |
| Démarrer automatiquement les conteneurs en arrière-plan | Il en va | Docker Compose | De nouveau pour améliorer les performances, Visual Studio crée un conteneur avec des montages de volume déjà prêts quand vous créez et exécutez votre conteneur. Si vous voulez contrôler le moment auquel est créé votre conteneur, désactivez cette option. |
| Tuer automatiquement les conteneurs lors de la fermeture de la solution | Il en va | Docker Compose | Désactivez cette option si vous voulez que les conteneurs de votre solution continuent à s’exécuter après la fermeture de la solution ou la fermeture de Visual Studio. |
| Ne pas demander l’approbation du certificat SSL localhost | Off | ASP.NET projets core 2.1 | Si le certificat SSL localhost n’est pas approuvé, Visual Studio vous invite à le faire chaque fois que vous exécutez votre projet, sauf si cette case est cochée. |
::: moniker-end

::: moniker range=">=vs-2019"

Le tableau suivant décrit les paramètres **généraux** :

| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Installer Docker Desktop si nécessaire | Je me demande | Projet unique, Docker Compose | Choisissez si vous voulez être invité si Docker Desktop n’est pas installé. |
| Certificat de confiance ASP.NET Core SSL | Je me demande | ASP.NET projets Core 2.x | Lorsqu’il est configuré à **Prompt Me**, si le certificat localhost SSL n’est pas fiable, Visual Studio invite chaque fois que vous exécutez votre projet. |

Le tableau suivant décrit les paramètres **Single Project** et **Docker Compose** :

| Nom | Paramètre par défaut | S'applique à | Description |
| -----|:---------------:|:----------:| ----------- |
| Tirer requis Images Docker sur le projet ouvert | True | Projet unique, Docker Compose | Pour améliorer les performances lors du chargement des projets, Visual Studio démarre une opération d’extraction Docker en arrière-plan de sorte que lorsque vous êtes prêt à exécuter votre code, l’image est déjà téléchargée ou en cours de téléchargement. Si vous ne faites que charger des projets et du code de navigation, vous pouvez **configurer** False pour éviter de télécharger des images de conteneurs dont vous n’avez pas besoin. |
| Exécuter des conteneurs sur le projet ouvert | True | Projet unique, Docker Compose | Encore une fois pour une performance accrue, Visual Studio crée un conteneur à l’avance afin qu’il soit prêt pour quand vous construisez et exécutez votre conteneur. Si vous voulez contrôler lorsque votre conteneur est créé, définissez **Faux**. |
| Arrêter les conteneurs sur le projet fermer | True | Projet unique et Docker Compose | Définissez-vous à **Faux** si vous souhaitez que les conteneurs pour votre solution continuent à fonctionner après la fermeture de la solution ou la fermeture de Visual Studio. |

::: moniker-end
> [!WARNING]
> Si le certificat localhost SSL n’est pas fiable, et vous cochez la case pour supprimer l’incitation, alors les demandes web HTTPS peuvent échouer au moment de l’exécution dans votre application ou service. Dans ce cas, décochez la case **Ne pas demander**, exécutez votre projet et confirmez l’approbation à l’invite.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur le travail avec des conteneurs dans Visual Studio dans cette [vue d’ensemble](overview.md).