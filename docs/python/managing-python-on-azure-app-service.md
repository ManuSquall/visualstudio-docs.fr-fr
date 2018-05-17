---
title: Configuration de Python sur Azure App Service
description: Guide pratique pour installer un interpréteur et des bibliothèques Python sur Azure App Service, et pour configurer correctement des applications web faisant référence à cet interpréteur.
ms.date: 09/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 9a71ea2210bfc6c56a235f194354c3279c8e7370
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service"></a>Comment configurer un environnement Python sur Azure App Service

[Azure App Service](https://azure.microsoft.com/services/app-service/) est une offre PaaS (Platform-as-a-Service) pour les applications web, qu’il s’agisse de sites accessibles via un navigateur, d’API REST utilisées par vos propres clients ou de traitement déclenché par un événement. App Service prend entièrement en charge l’utilisation de Python pour implémenter des applications.

Une prise en charge personnalisable de Python sur Azure App Service est fournie sous la forme d’un ensemble *d’extensions de site* App Service qui contiennent chacune une version spécifique du runtime Python. Vous pouvez alors installer les packages souhaités directement dans cet environnement, comme décrit dans cet article. En personnalisant l’environnement dans le service App Service lui-même, vous n’avez pas besoin gérer les packages dans vos projets d’application web ou de les charger avec le code de l’application.

> [!Tip]
> Bien que Python 2.7 et 3.4 soient installés par défaut sur App Service dans les dossiers racine du serveur, vous ne pouvez pas personnaliser ni installer des packages dans ces environnements, et vous ne devez pas dépendre de leur présence. Vous devez à la place vous appuyer sur une extension de site que vous contrôlez, comme décrit dans cet article.

> [!Important]
> Les processus décrits ici sont susceptibles de changer, notamment à des fins d’amélioration. Les modifications sont annoncées sur le [blog Python Engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Choix d’une version de Python via le portail Azure

1. Créez un service App Service pour votre application web sur le portail Azure.
1. Sur la page du service App Service, accédez à la section **Outils de développement**, sélectionnez **Extensions**, puis sélectionnez **+ Ajouter**.
1. Faites défiler la liste vers le bas jusqu’à l’extension qui contient la version de Python souhaitée :

    ![Portail Azure montrant les extensions Python](media/python-on-azure-extensions.png)

    > [!Tip]
    > Si vous avez besoin d’une version plus ancienne de Python et qu’elle ne figure pas dans les extensions de site, vous pouvez l’installer via Azure Resource Manager, comme décrit dans la section suivante.

1. Sélectionnez l’extension, acceptez les conditions juridiques, puis sélectionnez **OK**.
1. Une notification apparaît dans le portail quand l’installation est terminée.

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Choix d’une version de Python via Azure Resource Manager

Si vous déployez un service App Service avec un modèle Azure Resource Manager, ajoutez l’extension de site en tant que ressource. En particulier, l’extension apparaît sous forme de ressource imbriquée (un objet `resources` sous `resources`) avec le type `siteextensions` et le nom issu de [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Par exemple, après l’ajout d’une référence à `python361x64` (Python 3.6.1 x64), votre modèle peut ressembler à ceci (certaines propriétés étant omises) :

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="setting-webconfig-to-point-to-the-python-interpreter"></a>Définition de web.config pour le faire pointer vers l’interpréteur Python

Après avoir installé l’extension de site (via le portail ou un modèle Azure Resource Manager), vous faites ensuite pointer le fichier `web.config` de votre application vers l’interpréteur Python. Le fichier `web.config` indique au serveur web IIS (7+) qui s’exécute sur App Service comment il doit gérer les demandes Python via FastCGI ou HttpPlatform.

Commencez par rechercher le chemin complet du fichier `python.exe` de l’extension de site, puis créez et modifiez le fichier `web.config` approprié.

### <a name="finding-the-path-to-pythonexe"></a>Recherche du chemin de python.exe

Une extension de site Python est installée sur le serveur, sous `d:\home` dans un dossier approprié pour la version de Python et pour l’architecture (sauf dans le cas de quelques versions plus anciennes). Par exemple, Python 3.6.1 x64 est installé dans `d:\home\python361x64`. Le chemin complet de l’interpréteur Python est alors `d:\home\python361x64\python.exe`.

Pour voir le chemin d’accès spécifique de votre service App Service, sélectionnez **Extensions** dans la page App Service, puis sélectionnez l’extension dans la liste.

![Liste des extensions sur Azure App Service](media/python-on-azure-extension-list.png)

Cette action ouvre la page de description de l’extension, qui contient le chemin :

![Détails des extensions sur Azure App Service](media/python-on-azure-extension-detail.png)

Si vous avez des difficultés à voir le chemin pour l’extension, vous pouvez le trouver manuellement en utilisant la console :

1. Sur la page de votre service App Service, sélectionnez **Outils de développement > Console**.
1. Entrez la commande `ls ../home` ou `dir ..\home` pour afficher les dossiers d’extensions du plus haut niveau, comme `Python361x64`.
1. Entrez une commande comme `ls ../home/python361x64` ou `dir ..\home\python361x64` pour vérifier qu’il contient `python.exe` et les autres fichiers de l’interpréteur.

### <a name="configuring-the-fastcgi-handler"></a>Configuration du gestionnaire FastCGI

FastCGI est une interface qui fonctionne au niveau de la demande. IIS reçoit les connexions entrantes et transmet chaque demande à une application WSGI exécutée dans un ou plusieurs processus Python persistants. Comme le [package wfastcgi](https://pypi.io/project/wfastcgi) est préinstallé et configuré avec chaque extension de site Python, vous pouvez facilement l’activer en incluant le code dans `web.config`, comme ce qui est montré ci-dessous pour une application web basée sur le framework Bottle. Notez que les chemins complets de `python.exe` et de `wfastcgi.py` sont placés dans la clé `PythonHandler` :

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Les `<appSettings>` définis ici sont disponibles pour votre application en tant que variables d’environnement :

- La valeur de `PYTHONPATH` peut être librement étendue, mais elle doit inclure la racine de votre application.
- `WSGI_HANDLER` doit pointer vers une application WSGI importable à partir de votre application.
- `WSGI_LOG` est facultatif mais recommandé pour le débogage de votre application. 

Consultez [Publication sur Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) pour plus d’informations sur le contenu de `web.config` pour les applications Bottle, Flask et Django.

### <a name="configuring-the-httpplatform-handler"></a>Configuration du gestionnaire HttpPlatform

Le module HttpPlatform passe les connexions de socket directement à un processus Python autonome. Cette transmission vous permet d’exécuter n’importe quel serveur web de votre choix, mais nécessite un script de démarrage qui exécute un serveur web local. Vous spécifiez le script dans l’élément `<httpPlatform>` de `web.config`, où l’attribut `processPath` pointe vers l’interpréteur Python de l’extension de site et l’attribut `arguments` pointe vers votre script et les arguments que vous voulez fournir :

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

La variable d’environnement `HTTP_PLATFORM_PORT` montrée ici contient le port sur lequel votre serveur local doit écouter les connexions à partir de localhost. Cet exemple montre également comment créer une autre variable d’environnement si vous le souhaitez, dans ce cas `SERVER_PORT`.

## <a name="installing-packages"></a>Installation de packages

L’interpréteur Python installé via une extension de site n’est qu’une partie de votre environnement Python. Cela signifie que devez probablement installer aussi différents packages dans cet environnement.

Pour installer des packages directement dans l’environnement du serveur, utilisez une des méthodes suivantes :

| Méthodes | Utilisation |
| --- | --- |
| [Console Kudu d’Azure App Service](#azure-app-service-kudu-console) | Installe des packages de façon interactive. Les packages doivent être du Python pur ou doivent publier des wheels. |
| [API REST Kudu](#kudu-rest-api) | Peut être utilisée pour automatiser l’installation de packages.  Les packages doivent être du Python pur ou doivent publier des wheels. |
| Regrouper avec une application | Installez des packages directement dans votre projet, puis déployez-les sur App Service comme s’ils faisaient partie de votre application. Selon le nombre de dépendances et la fréquence de leur mise à jour, cette méthode peut représenter le moyen le plus simple de lancer un déploiement de travail. Notez que les bibliothèques doivent correspondre exactement à la version de Python sur le serveur. Dans le cas contraire, des erreurs incompréhensibles se produisent après le déploiement. Cela dit, comme les versions de Python dans les extensions de site App Service sont exactement les mêmes que celles publiées sur python.org, vous pouvez facilement obtenir une version compatible pour un développement local. |
| Environnements virtuels | Non pris en charge. Au lieu de cela, utilisez le regroupement et définissez la variable d’environnement `PYTHONPATH` pour qu’elle pointe vers l’emplacement des packages. |

### <a name="azure-app-service-kudu-console"></a>Console Kudu d’Azure App Service

La [console Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) vous donne un accès direct à partir d’une ligne de commande avec des privilèges élevés au serveur App Service et à son système de fichiers. Il s’agit d’un outil précieux pour le débogage, qui autorise en outre les opérations CLI, comme l’installation de packages.

1. Ouvrez Kudu depuis votre page App Service sur le portail Azure en sélectionnant **Outils de développement > Outils avancés**, puis en sélectionnant **OK**. Cette action accède à une URL qui est la même que l’URL de base de votre service App Service, excepté que `.scm` y est inséré. Par exemple, si votre URL de base est `https://vspython-test.azurewebsites.net/`, Kudu se trouve sur `https://vspython-test.scm.azurewebsites.net/` (que vous pouvez mettre en signet) :

    ![Console Kudu pour Azure App Service](media/python-on-azure-console01.png)

1. Sélectionnez **Console de débogage > CMD** pour ouvrir la console, dans laquelle vous pouvez naviguer dans votre installation de Python et voir les bibliothèques qui y figurent déjà.

1. Pour installer un package unique :

    a. Accédez au dossier de l’installation de Python où vous souhaitez installer le package, par exemple `d:\home\python361x64`.

    b. Utilisez `python.exe -m pip install <package_name>` pour installer un package.

    ![Exemple d’installation de Bottle via la console Kudu pour Azure App Service](media/python-on-azure-console02.png)

1. Si vous avez déjà déployé un fichier `requirements.txt` pour votre application sur le serveur, installez tous ces exigences comme suit :

    a. Accédez au dossier de l’installation de Python où vous souhaitez installer le package, par exemple `d:\home\python361x64`.

    b. Exécutez la commande `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    L’utilisation de `requirements.txt` est recommandée, car il est facile de reproduire exactement votre ensemble de packages à la fois localement et sur le serveur. N’oubliez pas de revenir à la console après avoir déployé des modifications apportées à `requirements.txt` et de réexécuter la commande.

> [!Note]
> Comme il n’y a pas de compilateur C sur App Service, vous devez installer le format wheel pour les packages avec des modules d’extension natifs. De nombreux packages populaires fournissent leur propre format wheel. Pour les packages qui ne le font pas, utilisez `pip wheel <package_name>` sur votre ordinateur de développement local, puis chargez le format wheel sur votre site. Vous trouverez un exemple sur la page [Gérer les packages requis avec requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>API REST Kudu

Au lieu d’utiliser la console Kudu via le portail Azure, vous pouvez exécuter des commandes à distance via l’API REST Kudu en publiant la commande sur `https://yoursite.scm.azurewebsites.net/api/command`. Par exemple, pour installer le package `bottle`, publiez le texte JSON suivant sur `/api/command` :

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Pour plus d’informations sur les commandes et l’authentification, consultez la [documentation Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Vous pouvez également voir des informations d’identification avec la commande `az webapp deployment list-publishing-profiles` via l’interface CLI Azure (consultez [az webapp deployment](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles)). Une bibliothèque helper pour la publication de commandes Kudu est disponible sur [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
