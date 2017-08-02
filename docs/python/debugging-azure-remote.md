---
title: "Débogage à distance Azure avec Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68fdc53-65a1-423c-8964-9815dbb3387e
caps.latest.revision: 1
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d2caa21359655a2079a853123baea31e471ba040
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---

# <a name="remotely-debugging-python-code-on-azure"></a>Débogage à distance de code Python sur Azure

[Prise en charge de Python dans Visual Studio](installation.md) permet de déboguer à distance le code Python qui s’exécute sur Azure App Service. Contrairement à un débogage à distance simple, la machine cible dans ce scénario n’est pas directement accessible par le biais de TCP. Visual Studio fournit donc un proxy qui expose le protocole de débogueur sur HTTP. Les projets créés à l’aide du modèle Web configurent automatiquement ce proxy dans le fichier `web.debug.config` généré. Le débogage à distance est également activé lorsque vous publiez une configuration de débogage de votre projet, comme décrit à la section [Publication sur Azure App Service](template-web.md#publishing-to-azure-app-service).

Étant donné que le débogage à distance Azure utilise des sockets web, vous devez activer les sockets pour votre App Service par le biais du [Portail Azure](https://portal.azure.com) en accédant à **Paramètres > Paramètres de l’application**, en définissant l’option **Paramètres généraux > Web sockets** sur **Activer**, puis en sélectionnant **Enregistrer** pour appliquer la modification. (Notez que les paramètres **Débogage** ne s’appliquent pas au débogage de Python.)

![Activation de sockets web dans le Portail Azure](~/python/media/azure-remote-debugging-enable-web-sockets.png)

Une fois que votre projet est correctement déployé et que les sockets web sont activés, vous pouvez effectuer l’attachement à App Service à partir de **l’Explorateur de serveurs** dans Visual Studio (**Affichage > Explorateur de serveurs**). Recherchez votre site sous **Azure > App Service** et le groupe de ressources applicable, cliquez avec le bouton droit, puis sélectionnez **Attacher le débogueur (Python)**. (Notez que la commande **Attacher le débogueur** pour les applications .NET s’exécutant sous IIS n’est utile que si vous co-hébergez un code .NET en même temps que votre application Python.)

Visual Studio peut vous diriger directement vers un ensemble d’instructions permettant d’effectuer un attachement direct, comme décrit ci-dessous à la section [Attachement sans l’Explorateur de serveurs](#attaching-without-server-explorer). Si la commande **Attacher le débogueur (Python)** n’apparaît pas ou que Visual Studio ne parvient pas à s’attacher à votre site, consultez [Résolution des problèmes du débogage distant Azure](debugging-azure-remote-troubleshooting.md).

Si l’attachement réussit, Visual Studio bascule vers un affichage de débogueur, et la barre d’outils doit indiquer le processus en cours de débogage tel qu’un URI `wss://` :

![Débogage d’un site web Azure App Service](~/python/media/azure-remote-debugging-attached.png)

Une fois l’attachement effectué, l’expérience de débogage est globalement identique à celle du débogage à distance standard soumis à quelques contraintes. En particulier, le serveur web IIS qui gère les demandes entrantes et les délègue au code Python par le biais de FastCGI présente un délai d’expiration de 90 secondes par défaut pour le traitement des demandes. Si le traitement d’une demande dure plus longtemps (par exemple, en raison de la suspension du processus au niveau d’un point d’arrêt), IIS terminera le processus, ce qui mettra immédiatement fin à votre session de débogage. 

## <a name="attaching-without-server-explorer"></a>Attachement sans l’Explorateur de serveurs

Pour attacher le débogueur directement à App Service, suivez les instructions fournies sur la page d’informations du proxy WebSocket que Visual Studio déploie sur votre site à l’adresse `<site_url>/ptvsd`, par exemple `ptvsdemo.azurewebsites.net/ptvsd`. La consultation de cette page vous permet également de vérifier que le proxy est correctement configuré :

![Page d’informations du proxy de débogage à distance Azure](~/python/media/azure-remote-debugging-proxy-info-page.png)

Comme indiqué, vous devrez construire une URL utilisant le secret de `web.debug.config`, qui est régénéré chaque fois que votre projet est publié. Ce fichier est masqué par défaut dans l’Explorateur de solutions et ne figure pas dans votre projet. Vous devrez donc afficher tous les fichiers ou ouvrir ce fichier dans un éditeur distinct. Après avoir ouvert le fichier, notez la valeur de l’élément appSetting nommé `WSGI_PTVSD_SECRET` :

![Détermination du point de terminaison du débogueur dans un Azure App Service](~/python/media/azure-remote-debugging-secret.png)

L’URL dont vous avez désormais besoin se présente sous la forme de la chaîne `wss://<secret>@<site_name>.azurewebsites.net/ptvsd`, dans laquelle vous devez bien sûr remplacer &lt;secret&gt; et &lt;site_name&gt; par vos propres valeurs.

Pour attacher le débogueur, sélectionnez **Débogage > Attacher au processus**, sélectionnez **Python remote debugging (Débogage à distance Python)** dans la zone déroulante **Transport**, entrez l’URL dans la zone de texte **Qualificateur**, puis appuyez sur Entrée. Si Visual Studio parvient à se connecter à App Service, il affiche un seul processus Python dans la liste. Sélectionnez-le, puis sélectionnez **Attacher** pour commencer le débogage :

![Utilisation de la boîte de dialogue Attacher au processus pour l’attachement à un site web Azure](~/python/media/azure-remote-debugging-manual-attach.png)

