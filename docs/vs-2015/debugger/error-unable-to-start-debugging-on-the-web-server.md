---
title: 'Erreur : Impossible de démarrer le débogage sur le serveur Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee62f07bd9fb4626f8e8fb3387e4b80ca2d903d7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652057"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Erreur : impossible de démarrer le débogage sur le serveur web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous essayez de déboguer une application ASP.NET exécutée sur un serveur Web, vous pouvez recevoir ce message d’erreur : Impossible de démarrer le débogage sur le serveur Web.
  
Dans de nombreux cas, cette erreur se produit, car IIS n’est pas configuré correctement.

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Vérifiez votre configuration d’IIS

Après avoir pris des mesures pour résoudre un problème détaillé ici et avant d’essayer à nouveau de déboguer, vous devrez peut-être également réinitialiser IIS. Vous pouvez le faire en ouvrant une invite de commandes administrateur et en tapant `iisreset`, ou vous pouvez le faire dans le Gestionnaire des services Internet. 

* Arrêter et redémarrer vos Pools d’applications, puis réessayez.

    Le Pool d’applications peut avoir arrêté ou une autre modification de configuration que vous avez apportées peut-être nécessiter que vous arrêtez et redémarrez votre Pool d’applications.
    
    > [!NOTE]
    > Si le Pool d’applications conserve l’arrêt, vous devrez désinstaller le Module de réécriture d’URL à partir du panneau, puis le réinstaller à l’aide du programme d’installation de plateforme Web (WPI). Cela peut être un problème après une mise à niveau du système significatives.

* Vérifiez votre configuration de Pool d’applications, corrigez-le si nécessaire, puis réessayez.

    Si les informations d’identification de mot de passe ont été modifiés, vous devrez peut-être les mettre à jour dans votre Pool d’applications. En outre, si vous avez récemment installé ASP.NET, le Pool d’applications peut être configuré pour une version incorrecte d’ASP.NET. Corrigez le problème et redémarrez le Pool d’applications.
    
* Vérifiez que votre dossier d’Application Web dispose des autorisations appropriées.

    Assurez-vous que vous donnez IIS_IUSRS ou IUSR (ou l’utilisateur spécifique associé au Pool d’Application) lecture et d’exécution des droits pour le dossier d’Application Web. Corrigez le problème et redémarrez votre Pool d’applications.

* Si vous utilisez un fichier d’hôtes avec les adresses locales, essayez d’utiliser l’adresse de bouclage au lieu de l’adresse IP de l’ordinateur.

* Afficher la page localhost dans le navigateur.

     Si IIS n’est pas installé correctement, vous devez obtenir des erreurs quand vous tapez `http://localhost` dans un navigateur.
     
     Pour plus d’informations sur le déploiement vers IIS, consultez [Remote Debugging ASP.NET sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou, pour ASP.NET Core, [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Assurez-vous que la version correcte d’ASP.NET est installée sur IIS.  Consultez [déployer une Application ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) ou, pour ASP.NET Core, [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Créer une application ASP.NET de base sur le serveur.

     Si vous ne pouvez pas obtenir votre application fonctionne avec le débogueur, essayez de créer une application ASP.NET de base localement sur le serveur et tentez de déboguer l’application de base. Si vous pouvez déboguer une application de base, qui peut vous aider à identifier quelle est la différence entre les deux configurations.
  
* Résoudre les erreurs d’authentification si vous utilisez uniquement l’adresse IP

     Par défaut, les adresses IP sont supposées faire partie d'Internet et l'authentification NTLM ne s'effectue pas via Internet. Si votre site web est configuré dans IIS pour exiger l’authentification, cette authentification échoue. Pour corriger ce problème, vous pouvez spécifier le nom de l’ordinateur distant au lieu de l’adresse IP.
     
## <a name="other-causes"></a>Autres causes

Si vous utilisez une version antérieure de Visual Studio :

- Redémarrez Visual Studio avec des privilèges élevés et réessayez.

    Un bogue dans les versions antérieures (corrigées plus tard) requis des privilèges élevés dans certains scénarios de débogage de ASP.NET.
    
- Si vous exécutez plusieurs instances de Visual Studio, ouvrez à nouveau votre projet dans une instance de Visual Studio et réessayez.

## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
