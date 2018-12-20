---
title: Configurer des applications web Python pour IIS
description: Guide pratique pour configurer des applications web Python afin de les exécuter avec Internet Information Services sur une machine virtuelle Windows.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 8de69c64cac5c841867f5d993395e5ab380625eb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062896"
---
# <a name="configure-python-web-apps-for-iis"></a>Configurer des applications web Python pour IIS

Si vous utilisez Internet Information Services (IIS) comme serveur web sur un ordinateur Windows (y compris une [machine virtuelle Windows sur Azure](/azure/architecture/reference-architectures/n-tier/windows-vm), les applications Python doivent comporter des paramètres spécifiques dans leur fichier *web.config* pour qu’IIS puisse traiter correctement le code Python. Python doit par ailleurs être installé sur l’ordinateur proprement dit, avec tous les packages requis par l’application web.

> [!Note]
> Cet article était auparavant une aide à la configuration de Python sur Azure App Service sous Windows. Les extensions Python et les hôtes Windows utilisés dans ce scénario sont maintenant déconseillés au profit d’Azure App Service sous Linux. Pour plus d’informations, voir [Publier des applications Python sur Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). L’article précédent, cependant, est toujours disponible sur [Gérer App Service sous Windows avec les extensions Python](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Installer Python sous Windows

Pour exécuter une application web, commencez par installer directement la version requise de Python sur l’ordinateur hôte Windows (voir [Installer des interpréteurs Python](installing-python-interpreters.md)).

Notez l’emplacement de l’interpréteur `python.exe` pour les étapes suivantes. Dans un souci de commodité, vous pouvez ajouter cet emplacement à votre variable d’environnement PATH.

## <a name="install-packages"></a>Installer des packages

Si vous vous servez d’un hôte dédié, vous pouvez utiliser l’environnement Python global pour exécuter votre application plutôt qu’un environnement virtuel. Il vous sera alors possible d’installer tous les éléments requis par votre application dans l’environnement global en exécutant simplement `pip install -r requirements.txt` dans une invite de commandes.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Définir web.config pour le faire pointer vers l’interpréteur Python

Le fichier *web.config* de votre application indique au serveur web IIS (7+) qui s’exécute sous Windows comment il doit gérer les requêtes Python avec FastCGI ou HttpPlatform. Si vous utilisez Visual Studio 2017, vous devez modifier *web.config* manuellement. Comme nous le décrivons dans une section ultérieure, Visual Studio 2015 effectue des modifications.

### <a name="configure-the-httpplatform-handler"></a>Configurer le gestionnaire HttpPlatform

Le module HttpPlatform passe les connexions de socket directement à un processus Python autonome. Cette transmission vous permet d’exécuter n’importe quel serveur web de votre choix, mais nécessite un script de démarrage qui exécute un serveur web local. Vous spécifiez le script dans l’élément `<httpPlatform>` de *web.config*, où l’attribut `processPath` pointe vers l’interpréteur Python de l’extension de site, et où l’attribut `arguments` pointe vers votre script et les arguments à fournir :

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
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

### <a name="configure-the-fastcgi-handler"></a>Configurer le gestionnaire FastCGI

FastCGI est une interface qui fonctionne au niveau de la demande. IIS reçoit les connexions entrantes et transmet chaque demande à une application WSGI exécutée dans un ou plusieurs processus Python persistants.

Pour l’utiliser, commencez par installer et configurer le package wfastcgi suivant les instructions de [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

Ensuite, modifiez le fichier *web.config* votre application en ajoutant les chemins d’accès complets à *python.exe* et à *wfastcgi.py* dans la clé `PythonHandler`. Les étapes ci-dessous supposent que Python est installé dans *C:\python36-32* et que le code de votre application se trouve dans *C:\home\site\wwwroot* ; adaptez ces emplacements à vos chemins :

1. Modifiez l’entrée `PythonHandler` dans *web.config* pour que le chemin corresponde à l’emplacement d’installation de Python (pour plus d’informations, voir [Informations de référence sur la configuration d’IIS](https://www.iis.net/configreference) (iis.net)).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Dans la section `<appSettings>` de *web.config*, ajoutez les clés de `WSGI_HANDLER`, `WSGI_LOG` (facultatif) et `PYTHONPATH` :

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Ces valeurs `<appSettings>` sont accessibles à votre application comme variables d’environnement :

    - La valeur de `PYTHONPATH` peut être librement étendue, mais elle doit inclure la racine de votre application.
    - `WSGI_HANDLER` doit pointer vers une application WSGI importable à partir de votre application.
    - `WSGI_LOG` est facultatif mais recommandé pour le débogage de votre application.

1. Définissez l’entrée `WSGI_HANDLER` dans *web.config* de manière appropriée pour le framework que vous utilisez :

    - **Bottle** : vérifiez la présence de parenthèses après `app.wsgi_app`, comme ci-dessous. Cela est nécessaire, car cet objet est une fonction (consultez *app.py*) et non une variable :

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask** : changez la valeur de `WSGI_HANDLER` en `<project_name>.app`, où `<project_name>` correspond au nom de votre projet. Vous pouvez trouver l’identificateur exact en examinant l’instruction `from <project_name> import app` dans *runserver.py*. Par exemple, si le projet est nommé « FlaskAzurePublishExample », l’entrée apparaît comme suit :

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django** : deux changements sont nécessaires dans *web.config* pour les projets Django. Commencez par changer la valeur `WSGI_HANDLER` en `django.core.wsgi.get_wsgi_application()` (l’objet se trouve dans le fichier *wsgi.py*) :

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Ensuite, ajoutez l’entrée suivante en dessous de celle de `WSGI_HANDLER`, en remplaçant `DjangoAzurePublishExample` par le nom de votre projet :

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Applications Django uniquement** : dans le fichier *settings.py* du projet Django, ajoutez votre domaine d’URL de site ou votre adresse IP à `ALLOWED_HOSTS`, comme indiqué ci-dessous, en remplaçant bien sûr « 1.2.3.4 » par votre URL ou votre adresse IP :

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Si vous ne parvenez pas à ajouter votre URL au tableau, vous obtenez l’erreur suivante : **DisallowedHost pour / En-tête HTTP_HOST non valide : « \<URL du site\> ». Vous devrez peut-être ajouter « \<URL du site\> » à ALLOWED_HOSTS.**

    Remarque : lorsque le tableau est vide, Django autorise automatiquement « localhost » et « 127.0.0.1 », mais le fait d’ajouter votre URL de production a pour effet de retirer ces autorisations. C’est la raison pour laquelle vous pouvez souhaiter conserver des copies de développement et de production distinctes de *settings.py*, ou utiliser des variables d’environnement pour contrôler les valeurs d’exécution.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Effectuer un déploiement sur IIS ou sur une machine virtuelle Windows

Maintenant que votre projet comporte le bon fichier *web.config*, vous pouvez lancer la publication sur l’ordinateur IIS en utilisant la commande **Publier** du menu contextuel du projet dans **l’Explorateur de solutions** et en sélectionnant l’option (**IIS, FTP, etc.**). Dans ce cas, Visual Studio copie simplement les fichiers projet sur le serveur ; vous êtes responsable de toute la configuration côté serveur.
