---
title: "Modèle de projet de service cloud Azure pour Python | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2ce82ee-8c73-419a-bbd2-4c3513fd394d
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: 5dd1c40c925327c9494e3a334cdf348692a4981d
ms.lasthandoff: 04/10/2017

---

# <a name="azure-cloud-service-projects-for-python"></a>Projets de service cloud Azure pour Python

Visual Studio fournit des modèles conçus pour vous aider à vous familiariser avec la création de services cloud Azure à l’aide de Python.

Un [service cloud](http://go.microsoft.com/fwlink/?LinkId=306052) se compose d’un nombre quelconque de *rôles de travail* et de *rôles web*, qui exécutent une tâche distincte sur le plan conceptuel, mais qui peuvent être répliqués séparément sur autant de machines virtuelles que nécessaire pour la mise à l’échelle. Les rôles web assurent l’hébergement des applications web frontales. Il est possible d’utiliser n’importe quel framework web prenant en charge WSGI pour écrire une application Python (prise en charge par le [modèle de projet web](template-web.md)). Les rôles de travail sont destinés aux longs processus qui n’interagissent pas directement avec les utilisateurs. Ils utilisent généralement les bibliothèques de [données](http://go.microsoft.com/fwlink/?LinkId=401571) et de [services d’application](http://go.microsoft.com/fwlink/?LinkId=401572), lesquelles peuvent être installées avec `pip install` &nbsp; [ `azure` ](http://pypi.org/project/azure).

Cette rubrique contient des détails sur le modèle de projet et les autres prises en charge dans Visual Studio 2017 (les versions antérieures sont similaires, mais présentent quelques différences). Pour plus d’informations sur l’utilisation d’Azure à partir de Python, visitez le [centre de développement Azure Python](http://go.microsoft.com/fwlink/?linkid=254360).

## <a name="create-a-project"></a>Créer un projet

1. Installez le [SDK Azure .NET pour Visual Studio](https://www.visualstudio.com/vs/azure-tools/) nécessaire pour utiliser le modèle Service cloud.
1. Dans Visual Studio, sélectionnez **Fichier > Nouveau > Projet...**, puis recherchez « Azure Python » et sélectionnez **Service cloud Azure** dans la liste :

    ![Modèle de projet cloud Azure pour Python](~/python/media/template-azure-cloud-project.png)

1. Sélectionnez un ou plusieurs rôles à inclure. Les projets cloud peuvent combiner des rôles écrits dans différents langages, ce qui signifie que vous pouvez facilement écrire chaque partie de votre application dans le langage le plus approprié. Pour ajouter de nouveaux rôles au projet après avoir renseigné cette boîte de dialogue, cliquez sur **Rôles** dans l’Explorateur de solutions et sélectionnez l’un des éléments sous **Ajouter**.

    ![Ajout de rôles dans le modèle de projet cloud Azure](~/python/media/template-azure-cloud-service-project-wizard.png)

1. Une fois les projets de rôles individuels créés, vous êtes invité à installer les packages Python supplémentaires, tels que les frameworks Django, Bottle ou Flask si vous avez sélectionné un rôle qui utilise l’un d’eux.

1. Après avoir ajouté un nouveau rôle à votre projet, vous obtenez des instructions de configuration. Celles-ci ne sont généralement pas nécessaires, mais elles peuvent être utiles pour personnaliser vos futurs projets. Notez que lors de l’ajout simultané de plusieurs rôles, seules les instructions correspondant au dernier rôle resteront ouvertes. Vous trouverez toutefois les instructions et les conseils de dépannage pour les autres rôles dans leurs fichiers `readme.mht` respectifs, qui se trouvent soit à la racine du rôle soit dans le dossier `bin`.

1. Le dossier `bin` d’un projet contient également un ou deux scripts PowerShell servant à configurer la machine virtuelle à distance, notamment l’installation de Python, tous les fichiers [requirements.txt](#dependencies) de votre projet ainsi que la configuration d’IIS, le cas échéant. Vous pouvez modifier ces fichiers comme vous le souhaitez pour votre déploiement, bien que vous puissiez gérer les options les plus courantes par d’autres moyens (voir [Configuration du déploiement des rôles](#configuring-role-deployment) ci-dessous). Nous vous déconseillons de supprimer ces fichiers, car un ancien script de configuration sera utilisé s’ils ne sont pas disponibles.

    ![Fichiers de prise en charge des rôles de travail](~/python/media/template-azure-cloud-service-worker-role-support-files.png)

    Pour ajouter ces scripts de configuration à un nouveau projet, cliquez avec le bouton droit sur le projet, sélectionnez **Ajouter > Nouvel élément...**, puis sélectionnez **Web Role Support Files** (Fichiers de prise en charge des rôles web) ou **Worker Role Support Files** (Fichiers de prise en charge des rôles de travail).
   

## <a name="configuring-role-deployment"></a>Configuration du déploiement des rôles

Les scripts PowerShell contenus dans le dossier `bin` d’un projet de rôle contrôlent le déploiement de ce rôle et peuvent être modifiés afin de personnaliser la configuration :

- `ConfigureCloudService.ps1` est utilisé pour les rôles web et de travail, généralement afin d’installer et configurer les dépendances et de définir la version de Python.
- `LaunchWorker.ps1` est utilisé uniquement pour les rôles de travail afin de modifier le comportement au démarrage, d’ajouter des arguments de ligne de commande ou d’ajouter des variables d’environnement.

Les deux fichiers contiennent des instructions de personnalisation. Vous pouvez également installer votre propre version de Python en ajoutant une autre tâche au fichier `ServiceDefinition.csdef` du projet de service cloud principal, en affectant la variable `PYTHON` au chemin `python.exe` (ou équivalent) qui est installé. Une fois `PYTHON` défini, Python ne sera pas installé à partir de NuGet.

Une configuration supplémentaire peut être obtenue comme suit :

1. Installez les packages à l’aide de `pip` en mettant à jour le fichier `requirements.txt` dans le répertoire racine de votre projet. Le script `ConfigureCloudService.ps1` installe ce fichier sur le déploiement.
1. Définissez les variables d’environnement en modifiant votre fichier `web.config` (rôles web) ou la section `Runtime` de votre fichier `ServiceDefinition.csdef` (rôles de travail).
1. Spécifiez le script et les arguments à utiliser pour un rôle de travail en modifiant la ligne de commande dans la section `Runtime/EntryPoint` de votre fichier `ServiceDefinitions.csdef`.
1. Définissez le script de gestionnaire principal correspondant à un rôle web à l’aide du fichier `web.config`.

## <a name="testing-role-deployment"></a>Test du déploiement des rôles

Lors de l’écriture de vos rôles, vous pouvez tester votre projet cloud en local à l’aide de l’émulateur Service cloud. Cet émulateur est fourni avec les outils du kit SDK Azure et représente une version limitée de l’environnement utilisé lorsque votre service cloud est publié dans Azure.

Pour démarrer l’émulateur, vérifiez d’abord que votre projet cloud correspond au projet de démarrage dans votre solution en cliquant avec le bouton droit et en sélectionnant **Définir comme projet de démarrage**. Sélectionnez **Déboguer > Démarrer le débogage** (F5) ou **Déboguer > Démarrer sans débogage** (Ctrl + F5).

Notez que certaines limitations de l’émulateur ne permettent pas de déboguer votre code Python. Nous vous recommandons donc de déboguer les rôles en les exécutant de façon indépendante, et d’utiliser ensuite l’émulateur pour effectuer les tests d’intégration avant la publication.


## <a name="deploying-a-role"></a>Déploiement d’un rôle

Pour ouvrir l’Assistant **Publication**, sélectionnez le projet de rôle dans l’Explorateur de solutions, puis sélectionnez **Génération > Publier** dans le menu principal ou cliquez avec le bouton droit sur le projet et sélectionnez **Publier**.

Le processus de publication implique deux phases. Tout d’abord, Visual Studio crée un package unique contenant tous les rôles de votre service cloud. Ce package correspond à ce qui est déployé sur Azure, qui initialise une ou plusieurs machines virtuelles pour chaque rôle et déploie la source.

À mesure que chaque machine virtuelle s’active, il exécute le script `ConfigureCloudService.ps1` et installe les dépendances. Ce script par défaut installe une version récente de Python à partir de [nuget](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) et tous les packages spécifiés dans un fichier `requirements.txt`. 

Pour finir, les rôles de travail exécutent `LaunchWorker.ps1`, qui démarre l’exécution de votre script Python ; les rôles web initialisent IIS et commencent à gérer les demandes web.


## <a name="dependencies"></a>Dépendances

Pour le service cloud, le script `ConfigureCloudService.ps1` utilise `pip` pour installer un jeu de dépendances Python. Celles-ci doivent être spécifiées dans un fichier nommé `requirements.txt` (personnalisable en modifiant `ConfigureCloudService.ps1`). Le fichier est exécuté avec `pip install -r requirements.txt` dans le cadre de l’initialisation.

Notez que les instances Service cloud n’incluent aucun compilateur C, ce qui signifie que toutes les bibliothèques avec des extensions C doivent fournir des binaires précompilés.

pip et ses dépendances, ainsi que les packages contenus dans le fichier `requirements.txt`, sont téléchargés automatiquement et peuvent être assimilés à l’utilisation de bande passante facturable. Consultez la page [Managing required packages](python-environments.md#managing-required-packages) (Gestion des packages requis) pour plus d’informations sur la gestion des fichiers `requirements.txt`.

## <a name="troubleshooting"></a>Résolution des problèmes

Si votre rôle web ou de travail ne se comporte pas correctement après le déploiement, vérifiez les points suivants :

- Votre projet Python inclut un dossier bin\ comprenant (au minimum) :
    - `ConfigureCloudService.ps1`
    - `LaunchWorker.ps1` (pour les rôles de travail)
    - `ps.cmd`

- Votre projet Python inclut un fichier `requirements.txt` répertoriant toutes les dépendances (ou bien une collection de fichiers wheels).
- Activez le Bureau à distance sur votre service cloud et examinez les fichiers journaux.
- Les journaux de `ConfigureCloudService.ps1` et `LaunchWorker.ps1` sont stockés dans le dossier `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles` de l’ordinateur distant.
- Les rôles web peuvent écrire des journaux supplémentaires sur un chemin d’accès configuré dans `web.config`, à savoir le chemin dans le paramètre d’application `WSGI_LOG`. La journalisation IIS ou FastCGI standard fonctionne également.
- Le fichier `LaunchWorker.ps1.log` est actuellement le seul moyen de visualiser la sortie ou les erreurs affichées par votre rôle de travail Python.
