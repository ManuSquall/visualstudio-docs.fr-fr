---
title: Modèle de projet de service cloud Azure pour Python
description: Visual Studio fournit des modèles pour les services cloud Azure écrits dans Python, y compris le déploiement des rôles, les dépendances et la résolution des problèmes.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 2de0f255da54d5bd8abf865f6534041d88bbbca3
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254834"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projets de service cloud Azure pour Python

Visual Studio fournit des modèles conçus pour vous aider à vous familiariser avec la création de services cloud Azure à l’aide de Python.

Un [service cloud](/azure/cloud-services/) se compose d’un nombre quelconque de *rôles de travail* et de *rôles web*, qui exécutent une tâche distincte sur le plan conceptuel, mais qui peuvent être répliqués séparément sur autant de machines virtuelles que nécessaire pour la mise à l’échelle. Les rôles web assurent l’hébergement des applications web frontales. En ce qui concerne Python, toute infrastructure Web qui prend en charge WSGI peut être utilisée pour écrire une telle application (prise en charge par le [modèle de projet Web](python-web-application-project-templates.md)). Les rôles de travail sont destinés aux longs processus qui n’interagissent pas directement avec les utilisateurs. Ils utilisent généralement les packages dans le package « Azure », qui est installé avec [`pip install azure`](https://pypi.org/project/azure) .

Cet article contient des détails sur le modèle de projet et les autres prises en charge dans Visual Studio 2017 et ultérieur (les versions antérieures sont similaires, mais présentent quelques différences). Pour plus d’informations sur l’utilisation d’Azure à partir de Python, visitez le [centre de développement Azure Python](/azure/python/).

## <a name="create-a-project"></a>Création d’un projet

1. Installez le [Kit de développement logiciel (SDK) Azure .net pour Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), qui est requis pour utiliser le modèle de service Cloud.
1. Dans Visual Studio, sélectionnez **fichier**  >  **nouveau**  >  **projet**, puis recherchez « Azure Python » et sélectionnez **service Cloud Azure** dans la liste :

    ![Modèle de projet cloud Azure pour Python](media/template-azure-cloud-project.png)

1. Sélectionnez un ou plusieurs rôles à inclure. Les projets cloud peuvent combiner des rôles écrits dans différents langages, ce qui signifie que vous pouvez facilement écrire chaque partie de votre application dans le langage le plus approprié. Pour ajouter de nouveaux rôles au projet après avoir terminé cette boîte de dialogue, cliquez avec le bouton droit sur **rôles** dans **Explorateur de solutions** et sélectionnez l’un des éléments sous **Ajouter**.

    ![Ajout de rôles dans le modèle de projet cloud Azure](media/template-azure-cloud-service-project-wizard.png)

1. Une fois les projets de rôles individuels créés, vous êtes invité à installer les packages Python supplémentaires, tels que les frameworks Django, Bottle ou Flask si vous avez sélectionné un rôle qui utilise l’un d’eux.

1. Après avoir ajouté un nouveau rôle à votre projet, des instructions de configuration s’affichent. Les modifications de configuration ne sont généralement pas nécessaires, mais peuvent être utiles pour personnaliser vos futurs projets. Notez que, lors de l’ajout simultané de plusieurs rôles, seules les instructions correspondant au dernier rôle restent ouvertes. Vous trouverez toutefois les instructions et les conseils de résolution des problèmes pour les autres rôles dans leurs fichiers *readme.mht* respectifs, soit à la racine du rôle, soit dans le dossier *bin*.

1. Le dossier *bin* d’un projet contient également un ou deux scripts PowerShell servant à configurer la machine virtuelle distante, notamment l’installation de Python, tous les fichiers [*requirements.txt*](#dependencies) de votre projet, ainsi que la configuration d’IIS, le cas échéant. Vous pouvez modifier ces fichiers comme vous le souhaitez pour votre déploiement. Toutefois, vous pouvez gérer les options les plus courantes par d’autres moyens (consultez [Configurer le déploiement des rôles](#configure-role-deployment) ci-dessous). Nous vous déconseillons de supprimer ces fichiers, car un ancien script de configuration est utilisé s’ils ne sont pas disponibles.

    ![Fichiers de prise en charge des rôles de travail](media/template-azure-cloud-service-worker-role-support-files.png)

    Pour ajouter ces scripts de configuration à un nouveau projet, cliquez avec le bouton droit sur le projet, sélectionnez **Ajouter**  >  **un nouvel élément**, puis sélectionnez **fichiers de support de rôle Web** ou **fichiers de prise en charge du rôle de travail**.

## <a name="configure-role-deployment"></a>Configurer le déploiement des rôles

Les scripts PowerShell contenus dans le dossier *bin* d’un projet de rôle contrôlent le déploiement de ce rôle et peuvent être modifiés pour personnaliser la configuration :

- *ConfigureCloudService.ps1* est utilisé pour les rôles web et de travail, généralement afin d’installer et de configurer les dépendances, et définir la version de Python.
- *LaunchWorker.ps1* est utilisé uniquement pour les rôles de travail afin de changer le comportement au démarrage, d’ajouter des arguments de ligne de commande ou d’ajouter des variables d’environnement.

Les deux fichiers contiennent des instructions de personnalisation. Vous pouvez également installer votre propre version de Python en ajoutant une autre tâche au fichier *ServiceDefinition.csdef* du projet de service cloud principal, et en affectant à la variable `PYTHON` le chemin du fichier *python.exe* (ou équivalent) installé. Quand `PYTHON` est défini, Python n’est pas installé à partir de NuGet.

Une configuration supplémentaire peut être obtenue comme suit :

1. Installez les packages à l’aide de `pip`, en mettant à jour le fichier *requirements.txt* dans le répertoire racine de votre projet. Le script *ConfigureCloudService.ps1* installe ce fichier au moment du déploiement.
1. Définissez les variables d’environnement en modifiant votre fichier *web.config* (rôles web) ou la section `Runtime` de votre fichier *ServiceDefinition.csdef* (rôles de travail).
1. Spécifiez le script et les arguments à utiliser pour un rôle de travail en modifiant la ligne de commande dans la section `Runtime/EntryPoint` de votre fichier *ServiceDefinitions.csdef*.
1. Définissez le script de gestionnaire principal pour un rôle web via le fichier *web.config*.

## <a name="test-role-deployment"></a>Tester le déploiement des rôles

Lors de l’écriture de vos rôles, vous pouvez tester votre projet cloud en local à l’aide de l’émulateur Service cloud. Cet émulateur est fourni avec les outils du kit SDK Azure et représente une version limitée de l’environnement utilisé quand votre service cloud est publié dans Azure.

Pour démarrer l’émulateur, vérifiez d’abord que votre projet cloud correspond au projet de démarrage dans votre solution en cliquant avec le bouton droit et en sélectionnant **Définir comme projet de démarrage**. **Sélectionnez ensuite déboguer**  >  **Démarrer le débogage** (**F5**) ou **Déboguer**  >  **exécuter sans débogage** (**CTRL** + **F5**).

Notez que certaines limitations de l’émulateur ne permettent pas de déboguer votre code Python. Nous vous recommandons donc de déboguer les rôles en les exécutant de façon indépendante, et d’utiliser ensuite l’émulateur pour effectuer les tests d’intégration avant la publication.

## <a name="deploy-a-role"></a>Déployer un rôle

Pour ouvrir l’Assistant **Publication**, sélectionnez le projet de rôle dans l’**Explorateur de solutions**, puis sélectionnez **Build** > **Publier** dans le menu principal, ou cliquez avec le bouton droit sur le projet, puis sélectionnez **Publier**.

Le processus de publication implique deux phases. Tout d’abord, Visual Studio crée un package unique contenant tous les rôles de votre service cloud. Ce package correspond à ce qui est déployé sur Azure, ce qui permet d’initialiser une ou plusieurs machines virtuelles pour chaque rôle et de déployer la source.

Une fois que chaque machine virtuelle s’active, il exécute le script *ConfigureCloudService.ps1* et installe les dépendances. Par défaut, ce script installe une version récente de Python à partir de [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22), ainsi que les packages spécifiés dans un fichier *requirements.txt*.

Pour finir, les rôles de travail exécutent *LaunchWorker.ps1*, qui démarre l’exécution de votre script Python. Les rôles web initialisent IIS et commencent à prendre en charge les requêtes web.

## <a name="dependencies"></a>Dépendances

Pour l’offre Services cloud, le script *ConfigureCloudService.ps1* utilise `pip` afin d’installer un ensemble de dépendances Python. Les dépendances doivent être spécifiées dans un fichier nommé *requirements.txt* (personnalisable en modifiant *ConfigureCloudService.ps1*). Le fichier est exécuté avec `pip install -r requirements.txt` dans le cadre de l’initialisation.

Notez que les instances de service cloud n’incluent aucun compilateur C, ce qui signifie que toutes les bibliothèques avec des extensions C doivent fournir des binaires précompilés.

pip et ses dépendances, ainsi que les packages contenus dans le fichier *requirements.txt*, sont téléchargés automatiquement et peuvent être pris en compte dans l’utilisation de la bande passante facturable. Consultez [Gérer les packages nécessaires](managing-required-packages-with-requirements-txt.md) pour plus d’informations sur la gestion des fichiers *requirements.txt*.

## <a name="troubleshooting"></a>Dépannage

Si votre rôle web ou de travail ne se comporte pas correctement après le déploiement, vérifiez les points suivants :

- Votre projet python comprend un *dossier \\ bin* avec (au moins) :

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (pour les rôles de travail)
  - *ps.cmd*

- Votre projet Python inclut un fichier *requirements.txt* qui liste toutes les dépendances (ou bien une collection de fichiers wheel).
- Activez le Bureau à distance sur votre service cloud et examinez les fichiers journaux.
- Les journaux de *ConfigureCloudService.ps1* et *LaunchWorker.ps1* sont stockés dans le dossier *C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles* sur l’ordinateur distant.
- Les rôles web peuvent écrire dans des journaux supplémentaires sur un chemin configuré dans *web.config*, à savoir le chemin dans le appSetting `WSGI_LOG`. La journalisation IIS ou FastCGI standard fonctionne également.
- Le fichier *LaunchWorker.ps1.log* est le seul moyen de visualiser la sortie ou les erreurs affichées par votre rôle de travail Python.
