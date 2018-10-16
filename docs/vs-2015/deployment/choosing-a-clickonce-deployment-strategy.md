---
title: Choix d’une stratégie de déploiement ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 54bf4f58a4cfe8622e12b3808ea9f36c8cf1ee49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175628"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Choix d'une stratégie de déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour déployer une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], trois stratégies sont possibles. Celle que vous choisissez dépend principalement du type d'application que vous déployez. Les trois stratégies de déploiement sont les suivantes :  
  
-   Installation à partir du Web ou d'un partage réseau  
  
-   Installation à partir d'un CD-ROM  
  
-   Démarrage de l'application à partir du Web ou d'un partage réseau  
  
    > [!NOTE]
    >  En plus de choisir une stratégie de déploiement, vous devez également choisir une stratégie de mise à jour de l'application. Pour plus d’informations, consultez [choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Installation à partir du Web ou d'un partage réseau  
 Cette stratégie permet de déployer votre application sur un serveur Web ou un partage de fichiers réseau. Lorsqu'un utilisateur final souhaite installer l'application, il clique sur une icône d'une page Web ou double-clique sur une icône du partage de fichiers. L'application est ensuite téléchargée, installée et démarrée sur l'ordinateur de l'utilisateur final. Les éléments sont ajoutés à la **Démarrer** menu et **Ajout / Suppression de programmes** dans **le panneau de configuration**.  
  
 Étant donné que cette stratégie dépend de la connexion réseau, elle fonctionne de manière optimale pour les applications qui seront déployées pour les utilisateurs qui ont accès à un réseau local ou une connexion Internet rapide.  
  
 Si vous déployez l’application à partir du Web, vous pouvez passer des arguments dans l’application lorsqu’elle est activée à l’aide d’une URL. Pour plus d’informations, consultez [Comment : récupérer des informations de chaîne de requête dans une Application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Vous ne pouvez pas passer d'arguments dans une application activée à l'aide de l'une des autres méthodes décrites dans ce document.  
  
 Pour activer cette stratégie de déploiement dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cliquez sur **à partir du Web** ou **à partir d’un fichier ou chemin d’accès lecteur UNC** sur le **comment installé** page de l’Assistant Publication.  
  
 Il s'agit de la stratégie de déploiement par défaut.  
  
## <a name="install-from-a-cd"></a>Installation à partir d'un CD-ROM  
 Cette stratégie permet de déployer votre application sur un média amovible tel qu'un CD-ROM ou un DVD. Comme avec l’option précédente, lorsque l’utilisateur choisit d’installer l’application, il est installé et démarré, et les éléments sont ajoutés à la **Démarrer** menu et **Ajout / Suppression de programmes** dans **contrôle Panneau**.  
  
 Cette stratégie fonctionne mieux dans le cas d'applications déployées sur les ordinateurs d'utilisateurs qui ne possèdent pas une connectivité réseau persistante ou qui ont des connexions à faible bande passante. L'application étant installée à partir d'un média amovible, aucune connexion réseau n'est nécessaire pour l'installation ; la connectivité réseau est néanmoins requise pour les mises à jour de l'application.  
  
 Pour activer cette stratégie de déploiement dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cliquez sur **à partir d’un CD-ROM ou DVD-ROM** sur le **comment installé** page de l’Assistant Publication.  
  
 Pour activer cette stratégie de déploiement manuellement, modifiez la **deploymentProvider** balise dans le manifeste de déploiement. (Dans Visual Studio, cette propriété est exposée en tant que **URL d’Installation** sur le **publier** page du Concepteur de projets. Il s’agit de Mage.exe **Start Location**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Démarrage de l'application à partir du Web ou d'un partage réseau  
 Cette stratégie est similaire à la première, sauf que l'application se comporte comme une application Web. Lorsque l’utilisateur clique sur un lien d’une page web (ou double-clique sur une icône du partage de fichiers), l’application est lancée. Lorsque les utilisateurs ferment l’application, il n’est plus disponible sur leur ordinateur local. rien n’est ajouté à la **Démarrer** menu ou **Ajout / Suppression de programmes** dans **le panneau de configuration**.  
  
> [!NOTE]
>  Techniquement, l'application est téléchargée et installée dans un cache d'application de l'ordinateur local, de la même façon qu'une application Web est téléchargée vers le cache Web. Comme pour le cache Web, les fichiers sont nettoyés du cache d'application en fin d'utilisation. Toutefois, l'utilisateur a l'impression que l'application est exécutée à partir du Web ou du partage de fichiers.  
  
 Cette stratégie fonctionne mieux avec des applications rarement utilisées, par exemple, un programme de calcul des avantages sociaux des employés, exécuté généralement une fois par an.  
  
 Pour activer cette stratégie de déploiement dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cliquez sur **ne pas installer l’application** sur le **installer ou exécuter à partir du Web** page de l’Assistant Publication.  
  
 Pour activer cette stratégie de déploiement manuellement, modifiez la **installer** balise dans le manifeste de déploiement. (Sa valeur peut être **true** ou **false**. Dans Mage.exe, utilisez le **en ligne uniquement** option dans le **Type d’Application** liste.)  
  
## <a name="web-browser-support"></a>Prise en charge du navigateur Web  
 Les applications destinées à .NET Framework 3.5 peuvent être installées à l'aide de n'importe quel navigateur.  
  
 Les applications destinées à .NET Framework 2.0 requièrent Internet Explorer.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)



