---
title: Débogage à distance Azure avec Python
description: Guide pratique pour configurer un Azure App Service pour utiliser Visual Studio pour le débogage à distance d’une application Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e3e70675901128ed6b8d118e54dc10ddee152a5
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008617"
---
# <a name="remotely-debug-python-code-on-azure"></a>Déboguer à distance du code Python sur Azure

[Prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md) permet de déboguer à distance le code Python qui s’exécute sur Azure App Service. Contrairement à un débogage à distance simple, l’ordinateur cible dans ce scénario n’est pas directement accessible par le biais de TCP. Visual Studio fournit donc un proxy qui expose le protocole de débogueur sur HTTP. Les projets créés à l’aide du modèle web configurent automatiquement ce proxy dans le fichier *web.debug.config* généré. Le débogage à distance est également activé quand vous publiez une configuration **Debug** de votre projet, comme décrit à la section [Publier sur Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

Étant donné que le débogage à distance Azure utilise des sockets web, vous devez activer les sockets pour votre App Service par le biais du [portail Azure](https://portal.azure.com) en accédant à **Paramètres** > **Paramètres de l’application**, en définissant l’option **Paramètres généraux** > **Web sockets** sur **Activer**, puis en sélectionnant **Enregistrer** pour appliquer la modification. (Notez que les paramètres **Débogage** ne s’appliquent pas au débogage de Python.)

![Activation de sockets web dans le Portail Azure](media/azure-remote-debugging-enable-web-sockets.png)

## <a name="attach-with-server-explorer"></a>Attacher avec l’Explorateur de serveurs

Une fois que votre projet est correctement déployé et que les sockets web sont activés, vous pouvez effectuer l’attachement à App Service à partir de **l’Explorateur de serveurs** dans Visual Studio (**Affichage** > **Explorateur de serveurs**). Recherchez votre site sous **Azure** > **App Service** et le groupe de ressources applicable, cliquez avec le bouton droit, puis sélectionnez **Attacher le débogueur (Python)**. (La commande **Attacher le débogueur** concerne les applications .NET s’exécutant sous IIS et n’est utile que si vous co-hébergez un code .NET en même temps que votre application Python.)

Visual Studio peut vous diriger directement vers un ensemble d’instructions permettant d’effectuer un attachement direct, comme décrit ci-dessous à la section [Attacher sans l’Explorateur de serveurs](#attach-without-server-explorer). Si la commande **Attacher le débogueur (Python)** n’apparaît pas ou que Visual Studio ne parvient pas à s’attacher à votre site, consultez [Résolution des problèmes de débogage à distance pour Python et Azure](debugging-remote-python-code-on-azure-troubleshooting.md).

Si l’attachement réussit, Visual Studio bascule vers une vue du débogueur. La barre d’outils indique le processus en cours de débogage tel qu’un URI `wss://` :

![Débogage d’un site web Azure App Service](media/azure-remote-debugging-attached.png)

Une fois l’attachement effectué, l’expérience de débogage est globalement identique à celle du débogage à distance standard soumis à quelques contraintes. En particulier, le serveur web IIS qui gère les demandes entrantes et les délègue au code Python par le biais de FastCGI présente un délai d’expiration de 90 secondes par défaut pour le traitement des demandes. Si le traitement d’une demande dépasse ce délai (par exemple, en raison de la suspension du processus au niveau d’un point d’arrêt), IIS termine le processus, ce qui met fin à votre session de débogage. 

## <a name="attach-without-server-explorer"></a>Attacher sans l’Explorateur de serveurs

Pour attacher le débogueur directement à App Service, suivez les instructions fournies dans la page d’informations du proxy WebSocket que Visual Studio déploie sur votre site à l’adresse *\<url_site>/ptvsd*, par exemple *ptvsdemo.azurewebsites.net/ptvsd*. La consultation de cette page vous permet également de vérifier que le proxy est correctement configuré :

![Page d’informations du proxy de débogage à distance Azure](media/azure-remote-debugging-proxy-info-page.png)

Comme indiqué, construisez une URL avec le secret de *web.debug.config*, qui est regénéré chaque fois que votre projet est publié. Ce fichier est masqué par défaut dans **l’Explorateur de solutions** et ne figure pas dans votre projet. Vous devez donc afficher tous les fichiers ou ouvrir ce fichier dans un éditeur distinct. Après avoir ouvert le fichier, examinez la valeur de l’élément appSetting nommé `WSGI_PTVSD_SECRET` :

![Détermination du point de terminaison du débogueur dans un Azure App Service](media/azure-remote-debugging-secret.png)

L’URL dont vous avez maintenant besoin se présente sous la forme `wss://<secret>@<site_name>.azurewebsites.net/ptvsd`, où vous devez remplacer &lt;secret&gt; et &lt;site_name&gt; par vos propres valeurs.

Pour attacher le débogueur, sélectionnez **Débogage** > **Attacher au processus**, sélectionnez **Python remote debugging** (Débogage à distance Python) dans la zone déroulante **Transport**, entrez l’URL dans la zone de texte **Qualificateur**, puis appuyez sur **Entrée**. Si Visual Studio parvient à se connecter à App Service, il affiche un seul processus Python dans la liste. Sélectionnez-le, puis sélectionnez **Attacher** pour commencer le débogage :

![Utilisation de la boîte de dialogue Attacher au processus pour l’attachement à un site web Azure](media/azure-remote-debugging-manual-attach.png)
