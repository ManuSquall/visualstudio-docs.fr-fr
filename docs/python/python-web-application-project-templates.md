---
title: Modèles d’application web pour Python
description: Visual Studio fournit des modèles pour les applications web Python qui utilisent des infrastructures Bottle, Flask et Django. La prise en charge inclut les configurations de débogage et la publication sur Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6553017034dc46cfd1c035564a83dde89d77d057
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254847"
---
# <a name="python-web-application-project-templates"></a>Modèles de projet d’application web Python

Python dans Visual Studio prend en charge le développement de projets web dans les frameworks Bottle, Django et Flask, via des modèles de projet et un lanceur de débogueur qui peuvent être configurés pour gérer différents frameworks. Ces modèles comprennent un fichier *requirements.txt* permettant de déclarer les dépendances nécessaires. Au moment de la création d’un projet à partir de l’un de ces modèles, Visual Studio vous invite à installer ces packages (voir [Installer les spécifications du projet](#install-project-requirements) plus loin dans cet article).

Vous pouvez également utiliser le modèle **Projet web** générique pour d’autres frameworks, comme Pyramid. Dans ce cas, aucun framework n’est installé avec le modèle. Installez plutôt les packages nécessaires dans l’environnement que vous utilisez pour le projet (consultez [Fenêtre Environnements Python - Onglet Package](python-environments-window-tab-reference.md#packages-tab)).

Pour plus d’informations sur le déploiement d’une application web Python sur Azure, consultez [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Utiliser un modèle de projet

Vous créez un projet à partir d’un modèle à l’aide de **fichier**  >  **nouveau**  >  **projet**. Pour afficher les modèles pour les projets Web, sélectionnez **python**  >  **Web** sur le côté gauche de la boîte de dialogue. Ensuite, sélectionnez un modèle de votre choix, en fournissant le nom du projet et de la solution, définissez les options d’un répertoire de solution et d’un dépôt Git, puis sélectionnez **OK**.

![Boîte de dialogue Nouveau projet pour les applications web](media/projects-new-project-dialog-web.png)

::: moniker range="<=vs-2017"

Le modèle générique **Projet web**, mentionné précédemment, propose un projet Visual Studio vide sans code et sans autre hypothèse mis à part qu’il s’agit d’un projet Python. Pour plus d’informations sur le modèle **Service cloud Azure**, consultez [Projets de service cloud Azure pour Python](python-azure-cloud-service-project-template.md).

::: moniker-end

::: moniker range=">=vs-2019"

Le modèle générique **Projet web**, mentionné précédemment, propose un projet Visual Studio vide sans code et sans autre hypothèse mis à part qu’il s’agit d’un projet Python.

::: moniker-end

Tous les autres modèles reposent sur les frameworks web Bottle, Flask ou Django et appartiennent à trois groupes généraux, comme décrit dans les sections qui suivent. Les applications créées à partir de l’un de ces modèles contiennent suffisamment de code pour exécuter et déboguer l’application localement. Chacun de ces modèles fournit également [l’objet d’application WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) nécessaire aux serveurs web de production.

### <a name="blank-group"></a>Groupe Vide

Tous les modèles de **\<framework> projet Web vides** créent un projet avec un code réutilisable plus ou moins faible et les dépendances nécessaires déclarées dans un fichier *requirements.txt* .

| Modèle | Description |
| --- | --- |
| **Projet web Bottle vide** | Génère une application minimale dans *app.py* avec une page d’accueil pour `/` et une page `/hello/<name>` qui répercute `<name>` en utilisant un modèle de page inline succinct. |
| **Projet web Django vide** | Génère un projet Django avec la structure de site Django de base mais aucune application Django. Pour plus d’informations, consultez [Modèles Django](python-django-web-application-project-template.md) et [Apprendre Django - Étape 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Projet web Flask vide** | Génère une application minimale contenant une page « Hello World! » unique pour `/`. Cette application est similaire au résultat obtenu en suivant les étapes détaillées dans [Démarrage rapide : Utiliser Visual Studio pour créer votre première application web Python](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Consultez également [Découvrir Flask - Étape 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Groupe web

Tous les modèles de **\<Framework> projet Web** créent une application Web de démarrage avec une conception identique, quelle que soit l’infrastructure choisie. Cette application contient les pages Accueil, À propos de et Contact, ainsi qu’une barre de navigation et une conception réactive grâce à Bootstrap. Chaque application est configurée de manière appropriée pour servir les fichiers statiques (CSS, JavaScript et polices) et utilise un mécanisme de modèle de page approprié pour le framework.

| Modèle | Description |
| --- | --- |
| **Projet web Bottle** | Génère une application dont les fichiers statiques sont contenus dans le dossier *static* et gérés par le biais de code dans *app.py*. Le routage des pages individuelles est contenu dans *routes.py* et le dossier *views* contient les modèles de page.|
| **Projet web Django** | Génère un projet Django et une application Django avec trois pages, la prise en charge de l’authentification et une base de données SQLite (mais aucun modèle de données). Pour plus d’informations, consultez [Modèles Django](python-django-web-application-project-template.md) et [Apprendre Django - Étape 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Projet web Flask** | Génère une application dont les fichiers statiques sont contenus dans le dossier *static*. Le code contenu dans *views.py* gère le routage, et les modèles de page utilisant le moteur Jinja sont contenus dans le dossier *templates*. Le fichier *runserver.py* fournit le code de démarrage. Consultez [Découvrir Flask - Étape 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Projet web Flask/Jade** | Génère la même application que le modèle de **projet Web** de la fiole, mais à l’aide de l’extension Jade pour le moteur de création de modèles Jinja. |

::: moniker range="vs-2017"
### <a name="polls-group"></a>Groupe Sondages

Les modèles de **\<framework> projet Web d’interrogation** créent une application Web de démarrage via laquelle les utilisateurs peuvent voter sur différentes questions de sondage. Chaque application repose sur la structure des modèles de projet **Web** pour utiliser une base de données afin de gérer les sondages et les réponses des utilisateurs. Les applications contiennent les modèles de données appropriés et une page d’application spéciale (/seed) qui charge les sondages à partir d’un fichier *samples.json*.

| Modèle | Description |
| --- | --- |
| **Projet web Bottle de sondage** | Génère une application qui peut s’exécuter sur une base de données en mémoire, MongoDB ou Stockage Table Azure, qui est configurée à l’aide de la variable d’environnement `REPOSITORY_NAME`. Les modèles de données et le code de magasin de données sont contenus dans le dossier *models* et le fichier *settings.py* contient le code permettant de déterminer quel magasin de données est utilisé. |
| **Projet web Django de sondage** | Génère un projet Django et une application Django contenant trois pages et une base de données SQLite. Inclut des personnalisations de l’interface administrative Django pour permettre à un administrateur authentifié de créer et de gérer des sondages. Pour plus d’informations, consultez [Modèles Django](python-django-web-application-project-template.md) et [Apprendre Django - Étape 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Projet web Flask de sondage** | Génère une application qui peut s’exécuter sur une base de données en mémoire, MongoDB ou Stockage Table Azure, qui est configurée à l’aide de la variable d’environnement `REPOSITORY_NAME`. Les modèles de données et le code de magasin de données sont contenus dans le dossier *models* et le fichier *settings.py* contient le code permettant de déterminer quel magasin de données est utilisé. L’application utilise le moteur Jinja pour les modèles de page. Consultez [Découvrir Flask - Étape 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Projet web Flask/Jade de sondage** | Génère la même application que le modèle de **projet Web de la fiole sondage** , mais à l’aide de l’extension Jade pour le moteur de création de modèles Jinja. |
::: moniker-end

## <a name="install-project-requirements"></a>Installer les spécifications du projet

Quand vous créez un projet à partir d’un modèle propre au framework, une boîte de dialogue s’affiche pour vous permettre d’installer les packages nécessaires à l’aide de pip. Nous vous recommandons également d’utiliser un [environnement virtuel](selecting-a-python-environment-for-a-project.md#use-virtual-environments) pour les projets Web afin que les dépendances appropriées soient incluses lorsque vous publiez votre site web :

![Boîte de dialogue installant les packages nécessaires pour un modèle de projet](media/template-web-requirements-txt-wizard.png)

Si vous utilisez le contrôle de code source, vous pouvez généralement ignorer le dossier d’environnement virtuel car cet environnement peut être recréé en utilisant uniquement *requirements.txt*. La meilleure façon d’exclure le dossier est de commencer par sélectionner l’option **I will install them myself** (Je les installerai moi-même) dans l’invite illustrée ci-dessus, puis de désactiver la validation automatique avant de créer l’environnement virtuel. Pour plus d’informations, consultez [Tutoriel d’apprentissage de Django - Étapes 1-2 et 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) et [Tutoriel d’apprentissage de Flask - Étapes 1-2 et 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Lors du déploiement sur Microsoft Azure App Service, sélectionnez une version de Python comme [extension de site](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) et installez manuellement les packages. En outre, étant donné qu’Azure App Service n’installe **pas** automatiquement les packages à partir d’un fichier *requirements.txt* en cas de déploiement à partir de Visual Studio, suivez les instructions de configuration fournies sur la page [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md).

::: moniker range="<=vs-2017"

Microsoft Azure Cloud Services *prend en charge* le fichier *requirements.txt*. Voir [Projets de service cloud Azure](python-azure-cloud-service-project-template.md) pour plus d’informations.

::: moniker-end

## <a name="debugging"></a>Débogage

Quand un projet web est démarré à des fins de débogage, Visual Studio démarre un serveur web local sur un port aléatoire et ouvre votre navigateur par défaut sur cette adresse et ce port. Pour spécifier des options supplémentaires, cliquez avec le bouton droit sur le projet, sélectionnez **Propriétés**, puis sélectionnez l’onglet **lanceur Web** :

![Propriétés du lanceur web pour le modèle web générique](media/template-web-launcher-properties.png)

Dans le groupe **Débogage** :

- **Chemins de recherche**, **Arguments de script**, **Arguments de l’interpréteur** et **Chemin de l’interpréteur** : ces options sont identiques à celles du [débogage standard](debugging-python-in-visual-studio.md).
- **URL de lancement** : spécifie l’URL qui est ouverte dans votre navigateur. Sa valeur par défaut est `localhost`.
- **Numéro de port** : port à utiliser si aucun n’est spécifié dans l’URL (Visual Studio sélectionne automatiquement un port par défaut). Ce paramètre vous permet de remplacer la valeur par défaut de la variable d’environnement `SERVER_PORT`, qui est utilisée par les modèles pour configurer le port écouté par le serveur de débogage local.

Les propriétés des groupes **Run Server Command** (Commande du serveur d’exécution) et **Debug Server Command** (Commande du serveur de débogage) (ce dernier apparaissant sous le contenu présenté par l’image) déterminent la façon dont le serveur web est lancé. Étant donné que de nombreux frameworks nécessitent l’utilisation d’un script à l’extérieur du projet actuel, il est possible de configurer le script à cet emplacement et de transmettre le nom du module de démarrage sous la forme d’un paramètre.

- **Commande** : il peut s’agir d’un script Python (fichier *\*.py*), d’un nom de module (par exemple, `python.exe -m module_name`) ou d’une simple ligne de code (telle que `python.exe -c "code"`). La valeur affichée dans la zone déroulante indique lequel de ces types est souhaité.
- **Arguments** : ces derniers sont transmis sur la ligne de commande derrière la commande.
- **Environnement**: liste de paires séparées par des sauts de ligne et \<NAME> = \<VALUE> spécifiant les variables d’environnement. Ces variables sont définies après toutes les propriétés susceptibles de modifier l’environnement, telles que le numéro de port et les chemins de recherche, et peuvent donc remplacer ces valeurs.

Toute propriété de projet ou variable d’environnement peut être spécifiée avec la syntaxe MSBuild, par exemple : `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` est le chemin d’accès relatif au fichier de démarrage, et `{StartupModule}` est le nom importable du fichier de démarrage. `$(SERVER_HOST)` et `$(SERVER_PORT)` sont des variables d’environnement normales définies par les propriétés d' **URL de lancement** et de **numéro de port** , automatiquement ou par la propriété d' **environnement** .

> [!Note]
> Les valeurs du groupe **Run Server Command** (Commande du serveur d’exécution) sont utilisées avec la commande **Débogage** > **Démarrer le serveur** ou **Ctrl**+**F5** ; les valeurs du groupe **Debug Server Command** (Commande du serveur de débogage) sont utilisées avec la commande **Débogage** > **Start Debug Server** (Démarrer le serveur de débogage) ou **F5**.

### <a name="sample-bottle-configuration"></a>Exemple de configuration Bottle

Le modèle de **projet Web Bottle** inclut un code réutilisable qui effectue la configuration nécessaire. Toutefois, une application Bottle importée peut ne pas inclure ce code, auquel cas les paramètres ci-après lancent l’application à l’aide du module `bottle` installé :

- Groupe **Run Server Command** (Commande du serveur d’exécution) :
  - **Commande**: `bottle` (module)
  - **Arguments**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Groupe **Debug Server Command** (Commande du serveur de débogage) :
  - **Commande**: `bottle` (module)
  - **Arguments** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

L’option `--reload` n’est pas recommandée en cas d’utilisation de Visual Studio pour le débogage.

### <a name="sample-pyramid-configuration"></a>Exemple de configuration Pyramid

Pour l’instant, la méthode de création recommandée pour les applications Pyramid consiste à utiliser l’outil en ligne de commande `pcreate`. Une fois qu’une application a été créée, elle peut être importée à l’aide du modèle [**de code python existant**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) . Après cela, sélectionnez la personnalisation **Projet web générique** pour configurer les options. Ces paramètres reposent sur l’hypothèse que Pyramid est installé dans un environnement virtuel à l’emplacement `..\env`.

- Groupe **Débogage** :
  - **Port du serveur** : 6543 (ou tout port configuré dans les fichiers *.ini*)

- Groupe **Run Server Command** (Commande du serveur d’exécution) :
  - Commande : `..\env\scripts\pserve-script.py` (script)
  - Arguments : `Production.ini`

- Groupe **Debug Server Command** (Commande du serveur de débogage) :
  - Commande : `..\env\scripts\pserve-script.py` (script)
  - Arguments : `Development.ini`

> [!Tip]
> Vous aurez probablement besoin de configurer la propriété **Répertoire de travail** de votre projet, car les applications Pyramid figurent généralement dans un dossier situé sous la racine du projet.

### <a name="other-configurations"></a>Autres configurations

Si vous disposez de paramètres pour un autre framework que vous souhaitez partager, ou si vous souhaitez demander des paramètres pour un autre framework, signalez le [problème sur GitHub](https://github.com/Microsoft/PTVS/issues).

::: moniker range="<=vs-2017"

## <a name="convert-a-project-to-azure-cloud-service"></a>Convertir un projet en projet Azure Cloud Service

La commande **convertir en Microsoft Azure projet de service Cloud** (image ci-dessous) ajoute un projet de service Cloud à votre solution. Ce projet comprend les paramètres de déploiement et la configuration pour les machines virtuelles et les services à utiliser. Utilisez la commande **Publier** sur le projet cloud à déployer sur Cloud Services. La commande **Publier** sur le projet Python effectue toujours le déploiement sur Sites web. Pour plus d’informations, consultez [projets de service Cloud Azure](python-azure-cloud-service-project-template.md).

![Commande Convertir en projet Microsoft Azure Cloud Service](media/template-web-convert-menu.png)

::: moniker-end

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les modèles d’élément Python](python-item-templates.md)
- [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)