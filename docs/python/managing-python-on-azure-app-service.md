---
title: Gestion de Python sur Azure App Service | Microsoft Docs
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 5b509a46dd3dbee3a45ab2eac57242636beee17b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---

# <a name="managing-python-on-azure-app-service"></a>Gestion de Python sur Azure App Service

[Azure App Service](https://azure.microsoft.com/services/app-service/) est une offre PaaS (Platform-as-a-Service) pour les applications web, qu’il s’agisse de sites accessibles via un navigateur, d’API REST utilisées par vos propres clients ou de traitement déclenché par un événement. App Service prend entièrement en charge l’utilisation de Python pour implémenter des applications.

La prise en charge de Python sur Azure App Service est fournie sous la forme d’un ensemble d’extensions de site App Service qui contiennent chacune une version spécifique du runtime Python. La dernière version de Python 3 est recommandée, bien sûr, mais vous pouvez choisir une version plus ancienne quand cela est nécessaire. Cette rubrique explique comment installer et configurer une extension de site, ainsi que tous les packages voulus.

> [!Note]
> Les processus décrits ici sont susceptibles de changer, notamment à des fins d’amélioration. Les modifications sont annoncées sur le [blog Python Engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Choix d’une version de Python via le portail Azure

Si votre site est déjà déployé et en cours d’exécution sur Azure App Service, accédez au panneau App Service, faites défiler jusqu’à la section **Outils de développement**, puis sélectionnez **Extensions > Ajouter**. Faites défiler la liste pour rechercher les extensions spécifiques de la version de Python que vous souhaitez. (Malheureusement, comme la liste ne peut pas être triée, les différentes versions sont souvent dispersées) :

![Portail Azure montrant les extensions Python](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Choix d’une version de Python via Azure Resource Manager

Si vous déployez votre site avec un modèle Azure Resource Manager, ajoutez l’extension de site en tant que ressource. L’extension apparaît sous la forme d’une ressource imbriquée de votre site avec le type `siteextensions` et le nom issu de [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Par exemple, après l’ajout d’une référence à `python361x64` (Python 3.6.1 x64), votre modèle peut ressembler à ce qui suit :

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
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
      ...
```

## <a name="configuring-your-site"></a>Configuration de votre site

Après avoir installé l’extension de site (via le portail ou un modèle Azure Resource Manager), le chemin d’installation de Python sera semblable à `d:\home\python361x64\python.exe`. Pour voir le chemin spécifique, sélectionnez l’extension dans la liste affichée pour App Service afin d’ouvrir la page de description contenant ce chemin :

![Liste des extensions sur Azure App Service](media/python-on-azure-extension-list.png)

![Détails des extensions sur Azure App Service](media/python-on-azure-extension-detail.png)

L’étape suivante consiste à faire référence à l’installation de Python dans le fichier `web.config` du site pour les gestionnaires de demandes de plateforme HTTP et FastCGI.

### <a name="using-the-fastcgi-handler"></a>Utilisation du gestionnaire FastCGI

FastCGI est une interface qui fonctionne au niveau de la demande. IIS reçoit les connexions entrantes et transmet chaque demande à une application WSGI exécutée dans un ou plusieurs processus Python persistants. Comme le [package wfastcgi](https://pypi.io/project/wfastcgi) est déjà installé et configuré avec chaque extension de site Python, vous pouvez facilement l’activer en incluant le code suivant dans `web.config` :

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Les `<appSettings>` sont disponibles pour votre application en tant que variables d’environnement :
- La valeur de `PYTHONPATH` peut être librement étendue, mais doit inclure la racine de votre site.
- `WSGI_HANDLER` doit pointer vers une application WSGI importable à partir de votre site.
- `WSGI_LOG` est facultatif, mais recommandé pour le débogage de votre site. 

Sous `<handlers>`, vérifiez que l’attribut `scriptProcessor` dans l’élément `<add>` contient les chemins appropriés à votre installation spécifique. Le chemin s’affiche à nouveau dans le panneau des détails de l’extension.

### <a name="using-the-http-platform-handler"></a>Utilisation du gestionnaire de plateforme HTTP

Le module HttpPlatform passe les connexions de socket directement à un processus Python autonome. Cette transmission vous permet d’exécuter n’importe quel serveur web de votre choix, mais nécessite un script de démarrage qui exécute un serveur web local. Vous spécifiez le script dans l’élément `<httpPlatform>`, où l’attribut `processPath` pointe vers Python et l’attribut `arguments` pointe vers votre script et tous les arguments que vous souhaitez fournir :

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

Le chemin d’accès à `python.exe` dans votre configuration est évidemment spécifique à la version que vous avez installée.

La variable d’environnement `HTTP_PLATFORM_PORT` indiquée dans le code contient le port sur lequel votre serveur local doit écouter les connexions à partir de localhost. Cet exemple montre également comment créer une autre variable d’environnement si vous le souhaitez, dans ce cas `SERVER_PORT`.

## <a name="installing-packages"></a>Installation de packages

Étant donné que votre application dépend probablement de plusieurs packages, vous devez vérifier que ces packages sont installés dans votre environnement Python sur App Service via l’une des trois méthodes suivantes :

- Console Azure App Service dans le portail Azure
- API REST Kudu
- Copie de chaque bibliothèque dans le code source d’application

### <a name="kudu-console"></a>Console Kudu

La [console Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) vous donne un accès direct à partir d’une ligne de commande avec des privilèges élevés au serveur App Service et à son système de fichiers. En plus d’être un outil de débogage précieux, elle peut également servir pour des configurations basées sur l’interface de ligne de commande.

Accédez à Kudu à partir du panneau App Service en sélectionnant **Outils de développement > Outils avancés**, puis **Go** (Atteindre) pour accéder à une URL qui est la même que votre URL App Service de base, avec l’ajout de `.scm`. Par exemple, si votre URL de base est `https://vspython-test.azurewebsites.net/`, Kudu se trouve sur `https://vspython-test.scm.azurewebsites.net/` :

![Console Kudu pour Azure App Service](media/python-on-azure-console01.png)

Sélectionnez **Console de débogage > CMD** pour ouvrir la console, dans laquelle vous pouvez naviguer dans votre installation de Python et voir les bibliothèques qui y figurent déjà.

Pour installer un package unique :

1. Accédez au dossier de l’installation de Python où vous souhaitez installer le package, par exemple `d:\home\python361x64`.
1. Utilisez `python.exe -m pip install <package_name>` pour installer un package.

![Exemple d’installation de matplotlib via la console Kudu pour Azure App Service](media/python-on-azure-console02.png)

Pour installer des packages à partir de `requirements.txt` (option recommandée) :

1. Accédez au dossier de l’installation de Python où vous souhaitez installer le package, par exemple `d:\home\python361x64`.
1. Utilisez `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` pour installer un package.

L’utilisation de requirements.txt est recommandée, car il est facile de reproduire votre ensemble exact de packages à la fois localement et sur le serveur.

> [!Note]
> Comme il n’existe aucun compilateur C sur votre serveur web, vous devez installer le format wheel pour tous les packages avec des modules d’extension natifs. De nombreux packages populaires fournissent leur propre format wheel. Pour les packages qui ne le font pas, utilisez `pip wheel <package_name>` sur votre ordinateur de développement local, puis chargez le format wheel sur votre site. Pour obtenir un exemple, consultez [Gestion des packages requis](python-environments.md#managing-required-packages)

### <a name="kudu-rest-api"></a>API REST Kudu

Au lieu d’utiliser la console Kudu via le portail Azure, vous pouvez exécuter des commandes à distance via l’API REST Kudu en publiant la commande sur `https://yoursite.scm.azurewebsites.net/api/command`. Par exemple, pour installer le package `matplotlib`, publiez le texte JSON suivant sur `/api/command` :

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

Pour plus d’informations sur les commandes et l’authentification, consultez la [documentation Kudu](https://github.com/projectkudu/kudu/wiki/REST-API). Vous pouvez également afficher des informations d’identification à l’aide de la commande [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) à partir de l’interface de ligne de commande Azure. Une bibliothèque d’assistance pour la publication des commandes Kudu est également disponible sur GitHub] (https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).


### <a name="copying-libraries-into-app-source-code"></a>Copie des bibliothèques dans le code source d’application

Au lieu d’installer des packages directement sur le serveur, vous pouvez à la place copier des bibliothèques dans votre propre code source et les déployer comme si elles faisaient partie de votre application. Selon le nombre de dépendances et la fréquence de leur mise à jour, cette méthode peut représenter le moyen le plus simple de lancer un déploiement de travail.

L’inconvénient est que ces bibliothèques doivent correspondre exactement à la version de Python sur le serveur, sinon des erreurs obscures s’affichent après le déploiement. Toutefois, étant donné que les versions de Python dans les extensions de site App Service sont exactement les mêmes que celles publiées sur python.org, vous pouvez facilement obtenir une version compatible pour le développement local.

### <a name="avoiding-virtual-environments"></a>Environnements virtuels déconseillés

Bien que l’utilisation d’un environnement virtuel localement peut vous aider à bien comprendre les dépendances nécessaires à votre site, elle n’est pas recommandée sur App Service. Au lieu de cela, installez simplement les bibliothèques dans le dossier Python principal et déployez-les avec votre application pour éviter d’avoir des dépendances en conflit.
