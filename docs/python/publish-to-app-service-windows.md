---
title: Publier une application Python sur Azure App Service sous Windows
description: Guide pratique pour publier directement une application web Python sur Azure App Service sous Windows à partir de Visual Studio, avec le contenu nécessaire au fichier web.config.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 9a3aee5dc1c2d1272c3814fa6cfb2561f6cb4564
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801306"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Publier sur Azure App Service sous Linux

> [!Note]
> Ce contenu et les fonctionnalités décrites sont déconseillés, mais continuent de fonctionner. Les développeurs Python sont invités à migrer vers [App Service sous Linux](publishing-python-web-applications-to-azure-from-visual-studio.md) dès que possible.

Visual Studio offre la possibilité de publier directement une application web Python sur Azure App Service sous Windows. Cela signifie copier les fichiers nécessaires sur le serveur et configurer un fichier `web.config` adapté qui indique au serveur web comment lancer votre application.

Le processus de publication diffère entre Visual Studio 2017 et ultérieur, et Visual Studio 2015. En particulier, Visual Studio 2015 automatise certaines des étapes, notamment la création de `web.config`, mais cette automatisation limite la flexibilité et le contrôle sur le long terme. Visual Studio 2017 et ultérieur nécessite plus d’étapes manuelles, mais offre un contrôle plus précis sur votre environnement Python. Les deux options sont décrites ici.

> [!Note]
> Pour plus d’informations sur les changements entre Visual Studio 2015 et Visual Studio 2017 et ultérieur, consultez le billet de blog [Publier sur Azure dans Visual Studio 2017](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Prérequis

Pour cette procédure pas à pas, vous avez besoin d’un projet d’application web basé sur les infrastructures Bottle, Flask ou Django. Si vous n’avez pas encore de projet et que voulez essayer le processus de publication, créez un projet de test simple comme suit :

1. Dans Visual Studio, sélectionnez **fichier > nouveau > projet**, recherchez « bouteille », sélectionnez le **projet Web Gourde**, spécifiez le nom et le chemin d’accès du projet, puis sélectionnez **OK**. (Le modèle Bottle est inclus dans la charge de travail de développement Python ; consultez [Installation](installing-python-support-in-visual-studio.md).)

1. Suivez les invites pour installer les packages externes, en sélectionnant **Installer dans un environnement virtuel** et votre interpréteur de base favori pour l’environnement virtuel. Vous faites généralement ce choix en fonction de la version de Python installée sur App Service.

1. Testez le projet localement en appuyant sur F5 ou en sélectionnant **Déboguer > Démarrer le débogage**.

## <a name="create-an-azure-app-service"></a>Créez un plan Azure App Service

La publication sur Azure nécessite un service App Service cible. Pour cela, vous pouvez créer un service App Service en utilisant un abonnement Azure ou vous pouvez utiliser un site temporaire.

Si vous n’avez pas d’abonnement, commencez avec un [compte Azure complet gratuit](https://azure.microsoft.com/free/), qui inclut des crédits importants pour les services Azure. Envisagez également de vous inscrire à [Visual Studio dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), qui vous donne un crédit de $25 par mois pendant une année complète.

> [!Tip]
> Azure demande une carte de crédit pour vérifier votre compte, mais la carte n’est pas débitée. Vous pouvez également définir une [limite de dépense](/azure/billing/billing-spending-limit) égale à vos crédits gratuits pour être sûr qu’il n’y aura aucun frais supplémentaire. En outre, Azure fournit un niveau de plan App Service gratuit qui est idéal pour les applications de test simples, comme celle qui décrite dans la section suivante.

### <a name="using-a-subscription"></a>Utilisation d’un abonnement

Avec un abonnement Azure actif, créez un service App Service avec une application web vide comme suit :

1. Connectez-vous à [portal.azure.com](https://portal.azure.com).
1. Sélectionnez **+Nouveau**, puis sélectionnez **Web + Mobile** et **Application web**.
1. Spécifiez un nom pour l’application web, laissez **Groupe de ressources** sur « Créer nouveau », puis choisissez **Windows** comme système d’exploitation.
1. Sélectionnez **Plan/emplacement App Service**, sélectionnez **Créer nouveau**, et spécifiez un nom et un emplacement. Sélectionnez ensuite **Niveau tarifaire**, faites défiler jusqu’à **F1 Gratuit** et sélectionnez-le, cliquez sur **Sélectionner**, sur **OK** puis sur **Créer**.
1. (Facultatif) Une fois que le service App Service a été créé, accédez à celui-ci, sélectionnez **Obtenir le profil de publication**, puis enregistrez le fichier localement.

### <a name="using-a-temporary-app-service"></a>Utilisation d’un service App Service temporaire

Pour créer un service App Service temporaire sans avoir besoin d’un abonnement Azure, procédez comme suit :

1. Ouvrez votre navigateur sur [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/) .
1. Sélectionnez **Application web** pour le type d’application, puis sélectionnez **Suivant**.
1. Sélectionnez **Site vide**, puis **Créer**.
1. Connectez-vous à l’aide de la connexion de réseau social de votre choix. Après un bref instant, votre site est prêt à l’adresse URL affichée.
1. Sélectionnez **Télécharger le profil de publication**, puis enregistrez le fichier `.publishsettings`, que vous utiliserez par la suite.

## <a name="configure-python-on-azure-app-service"></a>Configurer Python sur Azure App Service

Une fois que vous avez un service App Service avec une application web vide en cours d’exécution (dans votre abonnement ou sur un site gratuit), installez une version spécifique de Python comme décrit dans [Gestion de Python sur Azure App Service](managing-python-on-azure-app-service.md). Pour publier depuis Visual Studio 2017 et ultérieur, enregistrez le chemin exact de l’interpréteur Python installé avec l’extension de site, comme décrit dans cet article.

Si vous le souhaitez, vous pouvez également installer le package `bottle` en suivant le processus décrit dans ces instructions, car ce package est installé dans le cadre d’autres étapes de cette procédure pas à pas.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Publier sur App Service - Visual Studio 2017 et ultérieur

La publication sur Azure App Service à partir de Visual Studio 2017 et ultérieur copie seulement les fichiers de votre projet sur le serveur. Par conséquent, il est nécessaire de créer les fichiers nécessaires pour configurer l’environnement du serveur.

1. Dans Visual Studio **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et sélectionnez **Ajouter > nouvel élément...**. Dans la boîte de dialogue qui s’affiche, sélectionnez le modèle « Azure web.config (Fast CGI) », puis cliquez sur OK. Cette opération crée un fichier `web.config` dans le dossier racine de votre projet.

1. Modifiez l’entrée `PythonHandler` dans `web.config` afin que le chemin corresponde au chemin d’installation de Python sur le serveur (voir [Informations de référence sur IIS](https://www.iis.net/configreference) (iis.net) pour plus de détails). Par exemple, pour Python 3.6.1 x64, l’entrée doit être la suivante :

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Définissez l’entrée `WSGI_HANDLER` dans `web.config` de façon appropriée pour le framework que vous utilisez :

    - **Bottle** : ajoutez des parenthèses après `app.wsgi_app`, comme indiqué ci-dessous. Ceci est nécessaire, car cet objet est une fonction (voir `app.py`) et non pas une variable :

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask** : changez la valeur de `WSGI_HANDLER` en `<project_name>.app`, où `<project_name>` correspond au nom de votre projet. Vous pouvez trouver l’identificateur exact en examinant l’instruction `from <project_name> import app` dans `runserver.py`. Par exemple, si le projet est nommé « FlaskAzurePublishExample », l’entrée apparaît comme suit :

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django** : deux modifications sont nécessaires dans `web.config` pour les projets Django. Changez d’abord la valeur de `WSGI_HANDLER` en `django.core.wsgi.get_wsgi_application()` (l’objet est dans le fichier `wsgi.py`) :

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Ensuite, ajoutez l’entrée suivante en dessous de celle de `WSGI_HANDLER`, en remplaçant `DjangoAzurePublishExample` par le nom de votre projet :

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Uniquement pour les applications Django** : dans le fichier `settings.py` du projet Django, ajoutez votre domaine d’URL de site à `ALLOWED_HOSTS` comme illustré ci-dessous, en remplaçant « vspython-test-02.azurewebsites.net » par votre URL :

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Si vous n’ajoutez pas votre URL au tableau, l’erreur « DisallowedHost at/Invalid HTTP_HOST header : « » est générée \<site URL\> . Vous devrez peut-être ajouter « \<site URL\> » à ALLOWED_HOSTS.»

    Notez que lorsque le tableau est vide, Django autorise automatiquement « localhost », mais l’ajout de votre URL de production retire cette autorisation. Pour cette raison, vous pouvez souhaiter conserver des copies de développement et de production distinctes de `settings.py`, ou utiliser des variables d’environnement pour contrôler les valeurs d’exécution.

1. Dans **l’Explorateur de solutions**, développez le dossier portant le même que votre projet, cliquez avec le bouton droit sur le dossier `static`, sélectionnez **Ajouter > Nouvel élément...**, sélectionnez le modèle « web.config des fichiers statiques Azure » et sélectionnez **OK**. Cette action crée un autre élément `web.config` dans le dossier `static` qui désactive le traitement Python pour ce dossier. Cette configuration envoie des demandes de fichiers statiques au serveur web par défaut au lieu d’utiliser l’application Python.

1. Enregistrez votre projet puis, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet et sélectionnez **Publier**.

    ![Commande Publier du menu contextuel d’un projet](media/template-web-publish-command.png)

1. Sous l’onglet **Publier** qui apparaît, sélectionnez la cible de publication :

    a. Votre propre abonnement Azure : sélectionnez **Microsoft Azure App Service**, puis **Sélectionner** suivi de **Publier**. Une boîte de dialogue s’affiche, où vous pouvez sélectionner l’abonnement et le service App Service appropriés. Si le service App Service n’apparaît pas, utilisez le profil de publication téléchargé comme décrit ci-dessous pour un service App Service temporaire.

    ![Publier sur Azure, Étape 1, Visual Studio 2017 et ultérieur, abonnements existants](media/tutorials-common-publish-1a-2017.png)

    b. Si vous utilisez un App Service temporaire sur try.azurewebsites.net ou si vous devez utiliser un profil de publication, sélectionnez le **>** contrôle pour rechercher un **profil d’importation**, sélectionnez cette option, puis sélectionnez **publier**. L’emplacement du fichier `.publishsettings` précédemment téléchargé vous est alors demandé.

    ![Publier sur Azure, Étape 1, Visual Studio 2017 et ultérieur, App Service temporaire](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio affiche l’état de la publication dans une fenêtre « Activité de publication Web » et la fenêtre Publier. Une fois la publication terminée, le navigateur par défaut s’ouvre sur l’URL du site. L’URL apparaît également dans la fenêtre Publier.

1. Quand le navigateur s’ouvre, vous pouvez voir le message, « Impossible d’afficher la page, car une erreur interne au serveur s’est produite. » Ce message indique que votre environnement Python sur le serveur n’est pas entièrement configuré, auquel cas vous devez procéder comme suit :

    a. Reportez-vous à nouveau à [Gestion de Python sur Azure App Service](managing-python-on-azure-app-service.md) et vérifiez qu’une extension de site Python appropriée est installée.

    b. Vérifiez le chemin de l’interpréteur Python dans votre fichier `web.config`. Le chemin doit correspondre exactement à l’emplacement d’installation de l’extension de site que vous avez choisie.

    c. Utilisez la console Kudu pour mettre à niveau les packages répertoriés dans le fichier `requirements.txt` de votre application : accédez au même dossier Python que celui utilisé dans `web.config`, comme `/home/python361x64`, et exécutez la commande suivante, comme décrit dans la section [Console Kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) :

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Si vous voyez des erreurs d’autorisation lors de l’exécution de cette commande, vérifiez que vous exécutez la commande dans le dossier de votre extension de site et *non pas* dans le dossier de l’une des installations de Python par défaut du service App Service. Étant donné que vous ne pouvez pas modifier ces environnements par défaut, toute tentative d’installation de packages risque d’échouer.

    d. Pour une sortie d’erreur détaillée, ajoutez la ligne suivante à `web.config` dans le nœud `<system.webServer>` :

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Essayez en redémarrant le service App Service après l’installation de nouveaux packages. Un redémarrage n’est pas nécessaire lors de la modification de `web.config`, car App Service fait automatiquement un redémarrage quand `web.config` est modifié.

    > [!Tip]
    > Si vous apportez des modifications au fichier `requirements.txt` de votre application, veillez à utiliser à nouveau la console Kudu pour installer tous les packages désormais répertoriées dans ce fichier.

1. Une fois que vous avez entièrement configuré l’environnement de serveur, actualisez la page dans le navigateur afin que l’application web s’affiche.

    ![Résultats de la publication des applications Bottle, Flask et Django dans App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publication sur App Service - Visual Studio 2015

> [!Note]
> Vous pouvez trouver une courte vidéo de ce processus dans [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3 minutes 10 secondes).

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Publier**.

1. Dans la boîte de dialogue **Publier**, sélectionnez **Microsoft Azure App Service** :

  ![Publication sur Azure, étape 1](media/tutorials-common-publish-1.png)

1. Sélectionnez une cible :

    - Si vous disposez d’un abonnement Azure, sélectionnez **Microsoft Azure App Service** comme cible de publication, puis dans la boîte de dialogue suivante, sélectionnez un App Service existant ou sélectionnez **Nouveau** pour en créer un.
    - Si vous utilisez un site temporaire à partir de try.azurewebsites.net, sélectionnez **Importer** comme cible de publication, recherchez le fichier `.publishsettings` téléchargé à partir du site, puis sélectionnez **OK**.

1. Les détails d’App Service apparaissent dans l’onglet **Connexion** ci-dessous de la boîte de dialogue **Publier**.

  ![Publication sur Azure, étape 2](media/tutorials-common-publish-2.png)

1. Sélectionnez **Suivant >** autant de fois que nécessaire pour examiner les paramètres supplémentaires.

1. Sélectionnez **Publier**. Une fois votre application déployée sur Azure, votre navigateur par défaut s’ouvre au niveau de ce site.

Dans le cadre de ce processus, Visual Studio effectue également les étapes suivantes :

- Créer un fichier `web.config` sur le serveur, qui contient des pointeurs appropriés vers la fonction `wsgi_app` de l’application et vers l’interpréteur Python 3.4 par défaut d’App Service.
- Désactiver le traitement des fichiers dans le dossier `static` du projet (les règles concernées sont dans `web.config`).
- Publier l’environnement virtuel sur le serveur.
- Ajoutez un `web.debug.config` fichier et les outils de débogage pour activer le débogage distant. Pour Visual Studio 2019 version 16,4 et les versions antérieures, les outils de débogage sont ptvsd. Pour Visual Studio 2019 version 16,5 et versions ultérieures, les outils de débogage sont debugpy.

Comme indiqué précédemment, ces étapes automatiques simplifient le processus de publication, mais elles rendent plus difficile le contrôle de l’environnement Python. Par exemple, le fichier `web.config` est créé seulement sur le serveur, mais il n’est pas ajouté à votre projet. Le processus de publication prend aussi plus de temps, car il copie tout l’environnement virtuel à partir de votre ordinateur de développement, au lieu de s’appuyer sur la configuration du serveur.

Enfin, vous pouvez préférer gérer votre propre fichier `web.config` et utiliser `requirements.txt` pour gérer directement les packages sur le serveur. L’utilisation de `requirements.txt` garantit en particulier que vos environnements de développement et serveur correspondent toujours.
