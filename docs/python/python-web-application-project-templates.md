---
title: "Modèles d’application web pour Python dans Visual Studio | Microsoft Docs"
description: "Vue d’ensemble des modèles Visual Studio pour les applications web écrites dans Python à l’aide des infrastructures Bottle, Flask et Django, y compris les configurations de débogage et la publication sur Azure App Service."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: b75aae5811fa2410cf169d3401184b8af7ca381d
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="python-web-application-project-templates"></a>Modèles de projet d’application web Python

Python dans Visual Studio prend en charge le développement de projets web dans les frameworks Bottle, Django et Flask, via des modèles de projet et un lanceur de débogueur qui peuvent être configurés pour gérer différents frameworks. Vous pouvez également utiliser le modèle **Projet web** générique pour d’autres frameworks, comme Pyramid.

Visual Studio n’inclut pas les frameworks eux-mêmes. Vous devez les installer séparément en cliquant avec le bouton droit sur le projet et en sélectionnant **Python > Installer/mettre à niveau un framework...**.

Quand il est exécuté, un projet créé à partir d’un modèle (accessible par le biais des commandes **Fichier > Nouveau > Projet...**) lance un serveur web avec un port local sélectionné de façon aléatoire, ouvre votre navigateur par défaut lors du débogage et autorise une publication directe sur Microsoft Azure.

![Nouveaux modèles de projet web](media/template-web-new-project.png)

Les modèles Bottle, Flask et Django intègrent tous un site de démarrage avec plusieurs pages et fichiers statiques. Ce code est suffisant pour exécuter et déboguer le serveur localement (ce qui nécessite l’obtention de certains paramètres auprès de l’environnement) et pour effectuer un déploiement sur Microsoft Azure (exigeant la fourniture d’un objet [d’application WSGI](http://www.python.org/dev/peps/pep-3333/)).

Quand vous créez un projet à partir d’un modèle propre au framework, une boîte de dialogue s’affiche pour vous permettre d’installer les packages nécessaires à l’aide de pip. Nous vous recommandons également d’utiliser un [environnement virtuel](selecting-a-python-environment-for-a-project.md#using-virtual-environments) pour les projets Web afin que les dépendances appropriées soient incluses lorsque vous publiez votre site web :

![Boîte de dialogue installant les packages nécessaires pour un modèle de projet](media/template-web-requirements-txt-wizard.png)

Lors du déploiement sur Microsoft Azure App Service, sélectionnez une version de Python comme [extension de site](https://aka.ms/PythonOnAppService) et installez manuellement les packages. En outre, étant donné qu’Azure App Service n’installe **pas** automatiquement les packages à partir d’un fichier `requirements.txt` en cas de déploiement à partir de Visual Studio, suivez les instructions de configuration fournies sur la page [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

Microsoft Azure Cloud Services *prend* en charge le fichier `requirements.txt`. Pour plus d’informations, consultez l’article [Projets de service cloud Azure](python-azure-cloud-service-project-template.md).

## <a name="debugging"></a>Débogage

Quand un projet web est démarré à des fins de débogage, Visual Studio démarre le serveur web localement et ouvre votre navigateur par défaut au niveau de cette adresse et de ce port. Pour spécifier des options supplémentaires, cliquez avec le bouton droit sur le projet, sélectionnez **Propriétés**, puis sélectionnez l’onglet **Lanceur web** :

  ![Propriétés du lanceur web pour le modèle web générique](media/template-web-launcher-properties.png)

Dans le groupe **Débogage** :

- **Chemins de recherche**, **Arguments de script**, **Arguments de l’interpréteur** et **Chemin de l’interpréteur** : ces options sont identiques à celles du [débogage standard](debugging-python-in-visual-studio.md)
- **URL de lancement** : spécifie l’URL qui est ouverte dans votre navigateur. Ce champ est défini sur `localhost` par défaut.
- **Numéro de port** : port à utiliser si aucun n’est spécifié dans l’URL (Visual Studio sélectionne automatiquement un port par défaut). Ce paramètre vous permet de remplacer la valeur par défaut de la variable d’environnement `SERVER_PORT`, qui est utilisée par les modèles pour configurer le port écouté par le serveur de débogage local.

Les propriétés des groupes **Run Server Command** (Commande du serveur d’exécution) et **Debug Server Command** (Commande du serveur de débogage) (ce dernier apparaissant sous le contenu présenté par l’image) déterminent la façon dont le serveur web est lancé. Étant donné que de nombreux frameworks nécessitent l’utilisation d’un script à l’extérieur du projet actuel, il est possible de configurer le script à cet emplacement et de transmettre le nom du module de démarrage sous la forme d’un paramètre.

- **Commande** : il peut s’agir d’un script Python (fichier `*.py`), d’un nom de module (par exemple, `python.exe -m module_name`) ou d’une simple ligne de code (telle que `python.exe -c "code"`). La valeur affichée dans la zone déroulante indique lequel de ces types est souhaité.
- **Arguments** : ces derniers sont transmis sur la ligne de commande derrière la commande.
- **Environnement** : liste de paires `NAME=VALUE` séparées par un saut de ligne spécifiant les variables d’environnement. Ces variables sont définies après toutes les propriétés susceptibles de modifier l’environnement, telles que le numéro de port et les chemins de recherche, et peuvent donc remplacer ces valeurs.

Toute propriété de projet ou variable d’environnement peut être spécifiée avec la syntaxe MSBuild, par exemple : `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` est le chemin d’accès relatif au fichier de démarrage, et `{StartupModule}` est le nom importable du fichier de démarrage. `$(SERVER_HOST)` et `$(SERVER_PORT)` sont des variables d’environnement normales qui sont définies par les propriétés **URL de lancement** et **Numéro de port**, soit automatiquement, soit par la propriété **Environnement**.

> [!Note]
> Les valeurs du groupe **Run Server Command** (Commande du serveur d’exécution) sont utilisées avec la commande **Débogage > Démarrer le serveur** ou Ctrl-F5 ; les valeurs du groupe **Debog Server Command** (Commande du serveur de débogage) sont utilisées avec la commande **Débogage > Start Debug Server** (Démarrer le serveur de débogage) ou F5.

### <a name="sample-bottle-configuration"></a>Exemple de configuration Bottle

Le modèle de **projet Web Bottle** inclut un code réutilisable qui effectue la configuration nécessaire. Toutefois, une application Bottle importée peut ne pas inclure ce code, auquel cas les paramètres ci-après lancent l’application à l’aide du module `bottle` installé :

- Groupe **Run Server Command** (Commande du serveur d’exécution) :
  - **Commande** : `bottle` (module)
  - **Arguments** : `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Groupe **Debug Server Command** (Commande du serveur de débogage) :
  - **Commande** : `bottle` (module)
  - **Arguments** : `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

L’option `--reload` n’est pas recommandée en cas d’utilisation de Visual Studio pour le débogage.

### <a name="sample-pyramid-configuration"></a>Exemple de configuration Pyramid

Pour l’instant, la méthode de création recommandée pour les applications Pyramid consiste à utiliser l’outil en ligne de commande `pcreate`. Une fois qu’une application a été créée, elle peut être importée à l’aide du modèle [À partir de code Python existant](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files). Après cela, sélectionnez la personnalisation **Projet web générique** pour configurer les options. Ces paramètres reposent sur l’hypothèse que Pyramid est installé dans un environnement virtuel à l’emplacement `..\env`.

- Groupe **Débogage** :
  - **Port du serveur** : 6543 (ou tout port configuré dans les fichiers .ini)

- Groupe **Run Server Command** (Commande du serveur d’exécution) :
  - Commande : `..\env\scripts\pserve-script.py` (script)
  - Arguments : `Production.ini`

- Groupe **Debug Server Command** (Commande du serveur de débogage) :
    - Commande : `..\env\scripts\pserve-script.py` (script)
    - Arguments : `Development.ini`

> [!Tip]
> Vous aurez probablement besoin de configurer la propriété **Répertoire de travail** de votre projet, car les applications Pyramid figurent généralement dans un répertoire situé sous le premier niveau de l’arborescence source.

### <a name="other-configurations"></a>Autres configurations

Si vous disposez de paramètres pour un autre framework que vous souhaitez partager, ou si vous souhaitez demander des paramètres pour un autre framework, signalez le [problème sur GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Publication sur Azure App Service

Vous disposez de deux méthodes principales pour effectuer une publication sur Azure App Service. La première consiste à utiliser le déploiement à partir du contrôle de code source de la même façon que pour d’autres langages, comme décrit dans la [documentation Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Pour effectuer une publication directement à partir de Visual Studio, cliquez avec le bouton droit sur le projet, puis sélectionnez **Publier** :

![Commande Publier du menu contextuel d’un projet](media/template-web-publish-command.png)

Une fois que vous avez sélectionné la commande, un Assistant vous guide tout au long de la création d’un site web ou de l’importation de paramètres de publication, de l’aperçu des fichiers modifiés et de la publication sur un serveur distant.

Quand vous créez un site sur App Service, vous devez installer Python et tous les packages dont dépend votre site. Vous pouvez commencer par publier votre site, mais il ne s’exécutera qu’une fois que vous aurez configuré Python.

Pour installer Python sur App Service, nous vous recommandons d’utiliser les [extensions de site](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Ces extensions sont des copies des [versions officielles](https://www.python.org) de Python, optimisées et repackagées pour Azure App Service.

Une extension de site peut être déployée via le [portail Azure](https://portal.azure.com/). Sélectionnez le panneau **Outils de développement > Extensions** pour App Service, sélectionnez **Ajouter** et faites défiler la liste pour rechercher les éléments pour Python :

![Ajout d’une extension de site sur le Portail Azure](media/template-web-site-extensions.png)

Si vous utilisez des modèles de déploiement JSON, vous pouvez spécifier l’extension de site en tant que ressource de votre site :

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

Enfin, vous pouvez vous connecter par le biais de la [console de développement](https://github.com/projectkudu/kudu/wiki/Kudu-console) et installer une extension de site à partir de cette dernière.

Pour l’instant, la méthode recommandée pour installer des packages consiste à utiliser la console de développement après avoir installé l’extension de site et exécuté pip directement. Il est important que vous utilisiez le chemin d’accès complet à Python, sans quoi celui que vous exécutez risque d’être incorrect, et il n’est généralement pas nécessaire d’utiliser un environnement virtuel. Exemple :

```command
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Une fois déployé sur Azure App Service, votre site s’exécute derrière Microsoft IIS. Pour permettre à votre site de fonctionner avec IIS, vous devez ajouter au moins un fichier `web.config`. Vous disposez de modèles pour certaines cibles de déploiement courantes, auxquels vous pouvez accéder en cliquant avec le bouton droit sur le projet et en sélectionnant **Ajouter > Nouvel élément...** (voir la boîte de dialogue ci-dessous), et ces configurations peuvent être aisément modifiées pour d’autres utilisations. Pour plus d’informations sur les paramètres de configuration disponibles, consultez [Référence de configuration IIS](https://www.iis.net/configreference).

![Modèles d’élément Azure](media/template-web-azure-items.png)

Les éléments disponibles sont les suivants :

- web.config Azure (FastCGI) : ajoute un fichier `web.config` pour les cas dans lesquels votre application fournit un objet [WSGI](https://wsgi.readthedocs.io/en/latest/) pour gérer les connexions entrantes.
- web.config Azure (HttpPlatformHandler) : ajoute un fichier `web.config` pour les cas dans lesquels votre application écoute un socket pour les connexions entrantes.
- web.config des fichiers statiques Azure : quand vous disposez de l’un des fichiers `web.config` ci-dessus, ajoutez-le à un sous-répertoire pour qu’il ne soit pas traité par votre application.
- web.config de débogage à distance Azure : ajoute les fichiers nécessaires pour le débogage à distance sur WebSockets.
- Fichiers de support de rôle web : contiennent les scripts de déploiement par défaut pour les rôles web de service cloud.
- Fichiers de support de rôle de travail : contiennent les scripts de déploiement et de lancement par défaut pour les rôles de travail de service cloud.

Si vous ajoutez le modèle `web.config` de débogage à votre projet et que vous prévoyez d’utiliser le débogage à distance Python, vous devez publier le site dans la configuration « Debug ». Ce paramètre est distinct de la configuration de la solution active actuelle et est toujours défini par défaut sur la valeur « Release ». Pour modifier cette valeur, ouvrez l’onglet **Paramètres** et utilisez la zone de liste modifiable **Configuration** dans l’Assistant Publication (pour plus d’informations sur la création et le déploiement sur Azure Web Apps, consultez la [documentation Azure](https://azure.microsoft.com/develop/python/)) :

![Modification de la configuration de publication](media/template-web-publish-config.png)

La commande **Convertir en projet Microsoft Azure Cloud Service** (image ci-dessous) ajoute un projet de service cloud à votre solution. Ce projet comprend les paramètres de déploiement et la configuration pour les machines virtuelles et les services à utiliser. Utilisez la commande **Publier** sur le projet cloud à déployer sur Cloud Services. La commande **Publier** sur le projet Python effectue toujours le déploiement sur Sites web. Pour plus d’informations, consultez [Projets de service cloud Azure](python-azure-cloud-service-project-template.md).

![Commande Convertir en projet Microsoft Azure Cloud Service](media/template-web-convert-menu.png)
