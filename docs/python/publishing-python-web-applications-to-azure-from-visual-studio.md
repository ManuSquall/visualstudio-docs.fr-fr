---
title: Publication d’une application Python sur Azure App Service
description: Guide pratique pour publier une application web Python directement sur Azure App Service à partir de Visual Studio, y compris le contenu nécessaire pour le fichier web.config.
ms.date: 07/26/2018
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
ms.openlocfilehash: c42e87d6dcf4767621cafdb246294b8a45d0e4a7
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468668"
---
# <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

> [!Important]
> Le déploiement d’applications Python sur Azure App Service pour Linux n’est pas pris en charge à partir de Visual Studio. Microsoft prévoit également de déprécier Python sur App Service sur Windows. Des mises à jour seront publiées dans cet article quand elles seront disponibles. En attendant, vous pouvez effectuer un déploiement sur App Service sur Linux à l’aide de conteneurs. Pour plus d’informations, consultez [Déployer une application Web Python dans Web App pour conteneurs](/azure/app-service/containers/quickstart-python).

Visual Studio offre la possibilité de publier directement une application web Python sur Azure App Service. Publier sur Azure App Service signifie copier les fichiers nécessaires sur le serveur et configurer un fichier *web.config* approprié, qui indique au serveur web comment lancer votre application.

Le processus de publication diffère entre Visual Studio 2017 et Visual Studio 2015. Plus précisément, Visual Studio 2015 automatise certaines étapes, notamment la création de *web.config*, mais cette automation limite la flexibilité et le contrôle à long terme. Visual Studio 2017 nécessite plus d’étapes manuelles, mais offre un contrôle plus précis sur votre environnement Python. Les deux options sont décrites ici.

> [!Note]
> Pour plus d’informations sur les changements entre Visual Studio 2015 et Visual Studio 2017, consultez le billet de blog [Publier sur Azure dans Visual Studio 2017](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Prérequis

Pour cette procédure pas à pas, vous avez besoin d’un projet d’application web basé sur les infrastructures Bottle, Flask ou Django. Si vous n’avez pas encore de projet et que voulez essayer le processus de publication, créez un projet de test simple comme suit :

1. Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**, recherchez « Bottle », sélectionnez **Bottle Web Project** (Projet web Bottle), spécifiez un nom et un chemin pour le projet, puis cliquez sur **OK**. (Le modèle Bottle est inclus dans la charge de travail de développement Python ; consultez [Installation](installing-python-support-in-visual-studio.md).)

1. Suivez les invites pour installer les packages externes, en sélectionnant **Installer dans un environnement virtuel** et votre interpréteur de base favori pour l’environnement virtuel. Vous faites généralement ce choix en fonction de la version de Python installée sur App Service.

1. Testez le projet localement en appuyant sur **F5** ou en sélectionnant **Déboguer** > **Démarrer le débogage**.

## <a name="create-an-azure-app-service"></a>Créer un service Azure App Service

La publication sur Azure nécessite un service App Service cible. Pour cela, vous pouvez créer un service App Service en utilisant un abonnement Azure ou vous pouvez utiliser un site temporaire.

Si vous n’avez pas d’abonnement, commencez avec un [compte Azure complet gratuit](https://azure.microsoft.com/free/), qui inclut des crédits importants pour les services Azure. Envisagez également de vous inscrire à [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), qui vous offre 25 $ de crédit par mois pendant un an.

> [!Tip]
> Azure demande une carte de crédit pour vérifier votre compte, mais la carte n’est pas débitée. Vous pouvez également définir une [limite de dépense](/azure/billing/billing-spending-limit) égale à vos crédits gratuits pour être sûr qu’il n’y aura aucun frais supplémentaire. En outre, Azure fournit un niveau de plan App Service gratuit qui est idéal pour les applications de test simples, comme celle qui décrite dans la section suivante.

### <a name="use-a-subscription"></a>Utiliser un abonnement

Avec un abonnement Azure actif, créez un service App Service avec une application web vide comme suit :

1. Connectez-vous à [portal.azure.com](https://portal.azure.com).
1. Sélectionnez **+ Nouveau**, puis **Web + Mobile** et **Application web**.
1. Spécifiez un nom pour l’application web, laissez **Groupe de ressources** à **Créer**, puis choisissez **Windows** comme système d’exploitation.
1. Sélectionnez **Plan/emplacement App Service**, sélectionnez **Créer nouveau**, et spécifiez un nom et un emplacement. Sélectionnez ensuite **Niveau tarifaire**, faites défiler jusqu’à **F1 Gratuit** et sélectionnez-le, cliquez sur **Sélectionner**, sur **OK** puis sur **Créer**.
1. (Facultatif) Une fois que le service App Service a été créé, accédez à celui-ci, sélectionnez **Obtenir le profil de publication**, puis enregistrez le fichier localement.

### <a name="use-a-temporary-app-service"></a>Utiliser un service App Service temporaire

Pour créer un service App Service temporaire sans avoir besoin d’un abonnement Azure, procédez comme suit :

1. Ouvrez votre navigateur au niveau du site [try.azurewebsites.net](https://try.azurewebsites.net).
1. Sélectionnez **Application web** pour le type d’application, puis sélectionnez **Suivant**.
1. Sélectionnez **Site vide**, puis **Créer**.
1. Connectez-vous à l’aide de la connexion de réseau social de votre choix. Après un bref instant, votre site est prêt à l’adresse URL affichée.
1. Sélectionnez **Télécharger le profil de publication**, puis enregistrez le fichier *.publishsettings*, que vous allez utiliser par la suite.

## <a name="configure-python-on-azure-app-service"></a>Configurer Python sur Azure App Service

Une fois que vous avez un service App Service avec une application web vide en cours d’exécution (dans votre abonnement ou sur un site gratuit), installez une version spécifique de Python, comme indiqué dans [Gérer Python sur Azure App Service](managing-python-on-azure-app-service.md). Pour publier depuis Visual Studio 2017, enregistrez le chemin exact de l’interpréteur Python installé avec l’extension de site, comme décrit dans cet article.

Si vous le souhaitez, vous pouvez également installer le package `bottle` en suivant le processus décrit dans ces instructions, car ce package est installé dans le cadre d’autres étapes de cette procédure pas à pas.

## <a name="publish-to-app-service---visual-studio-2017"></a>Publier sur App Service - Visual Studio 2017

La publication sur Azure App Service à partir de Visual Studio 2017 copie seulement les fichiers de votre projet sur le serveur. Par conséquent, il est nécessaire de créer les fichiers nécessaires pour configurer l’environnement du serveur.

1. Dans **l’Explorateur de solutions** Visual Studio, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**. Dans la boîte de dialogue qui s’affiche, sélectionnez le modèle **Azure web.config (Fast CGI)**, puis sélectionnez **OK**. Cela entraîne la création d’un fichier *web.config* à la racine de votre projet.

1. Modifiez l’entrée `PythonHandler` dans *web.config* pour que le chemin corresponde à l’installation de Python sur le serveur (consultez [Informations de référence sur la configuration d’IIS](https://www.iis.net/configreference) (iis.net) pour plus de détails). Par exemple, pour Python 3.6.1 x64, l’entrée doit être la suivante :

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Définissez l’entrée `WSGI_HANDLER` dans *web.config* de manière appropriée pour le framework que vous utilisez :

    - **Bottle** : ajoutez des parenthèses après `app.wsgi_app`, comme indiqué ci-dessous. Cela est nécessaire, car cet objet est une fonction (consultez *app.py*) et non une variable :

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask** : changez la valeur de `WSGI_HANDLER` en `<project_name>.app`, où `<project_name>` correspond au nom de votre projet. Vous pouvez trouver l’identificateur exact en examinant l’instruction `from <project_name> import app` dans *runserver.py*. Par exemple, si le projet est nommé « FlaskAzurePublishExample », l’entrée apparaît comme suit :

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django** : deux changements sont nécessaires dans *web.config* pour les projets Django. Commencez par changer la valeur `WSGI_HANDLER` en `django.core.wsgi.get_wsgi_application()` (l’objet se trouve dans le fichier *wsgi.py*) :

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Ensuite, ajoutez l’entrée suivante en dessous de celle de `WSGI_HANDLER`, en remplaçant `DjangoAzurePublishExample` par le nom de votre projet :

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Uniquement pour les applications Django** : dans le fichier *settings.py* du projet Django, ajoutez votre domaine d’URL de site à `ALLOWED_HOSTS`, comme illustré ci-dessous, en veillant à remplacer « vspython-test-02.azurewebsites.net » par votre URL :

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Si vous ne parvenez pas à ajouter votre URL au tableau, vous obtenez l’erreur suivante : **DisallowedHost pour / En-tête HTTP_HOST non valide : « \<URL du site\> ». Vous devrez peut-être ajouter « \<URL du site\> » à ALLOWED_HOSTS.**

    Notez que lorsque le tableau est vide, Django autorise automatiquement « localhost », mais l’ajout de votre URL de production retire cette autorisation. C’est la raison pour laquelle vous pouvez souhaiter conserver des copies de développement et de production distinctes de *settings.py*, ou utiliser des variables d’environnement pour contrôler les valeurs d’exécution.

1. Dans l’**Explorateur de solutions**, développez le dossier portant le même nom que votre projet, cliquez avec le bouton droit sur le dossier **static**, sélectionnez **Ajouter** > **Nouvel élément**, sélectionnez le modèle **web.config des fichiers statiques Azure**, puis sélectionnez **OK**. Cette action crée un autre fichier *web.config* dans le dossier *static*, qui désactive le traitement de Python pour ce dossier. Cette configuration envoie des demandes de fichiers statiques au serveur web par défaut au lieu d’utiliser l’application Python.

1. Enregistrez votre projet puis, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet et sélectionnez **Publier**.

    ![Commande Publier du menu contextuel d’un projet](media/template-web-publish-command.png)

1. Sous l’onglet **Publier** qui apparaît, sélectionnez la cible de publication :

    1. Votre propre abonnement Azure : sélectionnez **Microsoft Azure App Service**, puis **Sélectionner** suivi de **Publier**. Une boîte de dialogue s’affiche, où vous pouvez sélectionner l’abonnement et le service App Service appropriés. Si le service App Service n’apparaît pas, utilisez le profil de publication téléchargé comme indiqué ci-dessous pour un service App Service temporaire.

       ![Publier sur Azure, Étape 1, Visual Studio 2017, abonnements existants](media/tutorials-common-publish-1a-2017.png)

    2. Si vous utilisez un service App Service temporaire sur try.azurewebsites.net, ou si vous devez utiliser un profil de publication, sélectionnez le contrôle **\>** pour rechercher **Importer un profil**, sélectionnez cette option, puis sélectionnez **Publier**. L’emplacement du fichier *.publishsettings* téléchargé vous est alors demandé.

    ![Publier sur Azure, Étape 1, Visual Studio 2017, service App Service temporaire](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio affiche l’état de la publication dans une fenêtre **Activité de publication web** et la fenêtre **Publier**. Une fois la publication terminée, le navigateur par défaut s’ouvre sur l’URL du site. L’URL apparaît également dans la fenêtre **Publier**.

1. Quand le navigateur s’ouvre, vous voyez éventuellement le message **Impossible d’afficher la page, car une erreur de serveur interne s’est produite.** Ce message indique que votre environnement Python sur le serveur n’est pas entièrement configuré, auquel cas vous devez procéder comme suit :

    1. Consultez à nouveau à [Gérer Python sur Azure App Service](managing-python-on-azure-app-service.md), et vérifiez qu’une extension de site Python appropriée est installée.

    2. Vérifiez soigneusement le chemin de l’interpréteur Python dans votre fichier *web.config*. Le chemin doit correspondre exactement à l’emplacement d’installation de l’extension de site que vous avez choisie.

    3. Utilisez la console Kudu pour mettre à niveau les packages listés dans le fichier *requirements.txt* de votre application : accédez au même dossier Python que celui utilisé dans *web.config*, par exemple */home/python361x64*, puis exécutez la commande suivante, comme indiqué dans la section [Console Kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) :

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Si vous voyez des erreurs d’autorisation lors de l’exécution de cette commande, vérifiez que vous exécutez la commande dans le dossier de votre extension de site et *non pas* dans le dossier de l’une des installations de Python par défaut du service App Service. Étant donné que vous ne pouvez pas modifier ces environnements par défaut, toute tentative d’installation de packages risque d’échouer.

    4. Pour une sortie d’erreur détaillée, ajoutez la ligne suivante à *web.config* dans le nœud `<system.webServer>` :

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    5. Essayez en redémarrant le service App Service après l’installation de nouveaux packages. Vous n’avez pas besoin de faire un redémarrage après avoir changé *web.config*, car App Service effectue automatiquement un redémarrage quand des changements sont apportés à *web.config*.

    > [!Tip]
    > Si vous apportez des changements au fichier *requirements.txt* de votre application, veillez à réutiliser la console Kudu pour installer les packages qui figurent désormais dans ce fichier.

1. Une fois que vous avez entièrement configuré l’environnement du serveur, actualisez la page dans le navigateur pour faire apparaître l’application web.

    ![Résultats de la publication d’applications Bottle, Flask et Django sur App Service](media/azure-publish-results.png)

## <a name="publish-to-app-service---visual-studio-2015"></a>Publier sur App Service - Visual Studio 2015

> [!Note]
> Vous pouvez trouver une courte vidéo de ce processus dans [Visual Studio Python tutorial: Building a website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3 min 10 s).

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Publier**.

1. Dans la boîte de dialogue **Publier**, sélectionnez **Microsoft Azure App Service** :

  ![Publication sur Azure, étape 1](media/tutorials-common-publish-1.png)

1. Sélectionnez une cible :

    - Si vous disposez d’un abonnement Azure, sélectionnez **Microsoft Azure App Service** comme cible de publication, puis dans la boîte de dialogue suivante, sélectionnez un App Service existant ou sélectionnez **Nouveau** pour en créer un.
    - Si vous utilisez un site temporaire à partir de try.azurewebsites.net, sélectionnez **Importer** en tant que cible de publication, recherchez le fichier *.publishsettings* téléchargé à partir du site, puis sélectionnez **OK**.

1. Les détails d’App Service apparaissent dans l’onglet **Connexion** ci-dessous de la boîte de dialogue **Publier**.

  ![Publication sur Azure, étape 2](media/tutorials-common-publish-2.png)

1. Sélectionnez **Suivant** autant de fois que nécessaire pour passer en revue les paramètres supplémentaires. Si vous prévoyez de [déboguer à distance votre code Python sur Azure](debugging-remote-python-code-on-azure.md), vous devez définir **Configuration** sur **Débogage**.

1. Sélectionnez **Publier**. Une fois votre application déployée sur Azure, votre navigateur par défaut s’ouvre au niveau de ce site.

Dans le cadre de ce processus, Visual Studio effectue également les étapes suivantes :

- Créer un fichier *web.config* sur le serveur, qui contient les pointeurs appropriés vers la fonction `wsgi_app` de l’application et vers l’interpréteur Python 3.4 par défaut d’App Service
- Désactiver le traitement des fichiers dans le dossier *static* du projet (les règles correspondantes sont dans *web.config*)
- Publier l’environnement virtuel sur le serveur.
- Ajouter un fichier *web.debug.config* et les outils de débogage ptvsd pour activer le débogage à distance

Comme indiqué précédemment, ces étapes automatiques simplifient le processus de publication, mais elles rendent plus difficile le contrôle de l’environnement Python. Par exemple, le fichier *web.config* est créé uniquement sur le serveur, mais il n’est pas ajouté à votre projet. Le processus de publication prend aussi plus de temps, car il copie tout l’environnement virtuel à partir de votre ordinateur de développement, au lieu de s’appuyer sur la configuration du serveur.

Enfin, vous pouvez préférer gérer votre propre fichier *web.config* et utiliser *requirements.txt* pour gérer directement les packages sur le serveur. Plus précisément, l’utilisation de *requirements.txt* permet de garantir la correspondance entre vos environnements de développement et serveur.

## <a name="remote-debugging-on-azure-app-service"></a>Débogage distant sur Azure App Service

Quand vous publiez une configuration **Debug** à partir de Visual Studio 2015, le processus crée automatiquement un fichier *web.debug.config*, et ajoute un dossier *ptvsd* contenant les outils de débogage nécessaires.

Avec Visual Studio 2017, au lieu de cela, vous ajoutez ces composants directement au projet. Cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, sélectionnez **Ajouter** > **Nouvel élément**, puis sélectionnez le modèle **Fichier web.config de débogage Azure Remote**. Un fichier de débogage *web.debug.config* et le dossier des outils *ptvsd* apparaissent dans votre projet.

Une fois que ces fichiers sont déployés sur le serveur (automatiquement avec Visual Studio 2015 ; lors de votre publication suivante avec Visual Studio 2017), vous pouvez suivre les instructions pour le [débogage distant Azure](debugging-remote-python-code-on-azure.md).
