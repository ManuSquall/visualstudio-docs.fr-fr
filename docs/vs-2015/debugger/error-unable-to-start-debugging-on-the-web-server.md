---
title: 'Erreur : impossible de démarrer le débogage sur le serveur Web | Microsoft Docs'
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
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185484"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Erreur : impossible de démarrer le débogage sur le serveur web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous essayez de déboguer une application ASP.NET exécutée sur un serveur web, le message d’erreur suivant peut s’afficher : Impossible de démarrer le débogage sur le serveur web.
  
Dans de nombreux cas, cette erreur se produit car IIS n’est pas configuré correctement.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Vérifier la configuration d’IIS

Après avoir pris les mesures nécessaires pour résoudre un problème détaillé ici, et avant de réessayer de déboguer, vous devrez peut-être également réinitialiser IIS. Pour ce faire, vous pouvez ouvrir une invite de commandes administrateur et taper `iisreset` , ou vous pouvez le faire dans le gestionnaire des services Internet. 

* Arrêtez et redémarrez vos pools d’applications, puis réessayez.

    Le pool d’applications a peut-être été arrêté ou une autre modification de configuration que vous avez apportée peut nécessiter l’arrêt et le redémarrage de votre pool d’applications.
    
    > [!NOTE]
    > Si le pool d’applications continue à s’arrêter, vous devrez peut-être désinstaller le module de réécriture d’URL du panneau de configuration, puis le réinstaller à l’aide de l’Web Platform Installer (WPI). Il peut s’agir d’un problème après une mise à niveau importante du système.

* Vérifiez la configuration de votre pool d’applications, corrigez-la si nécessaire, puis réessayez.

    Si les informations d’identification du mot de passe ont changé, vous devrez peut-être les mettre à jour dans votre pool d’applications. En outre, si vous avez récemment installé ASP.NET, le pool d’applications peut être configuré pour une version incorrecte de ASP.NET. Corrigez le problème et redémarrez le pool d’applications.
    
* Vérifiez que le dossier de votre application Web dispose des autorisations appropriées.

    Veillez à donner à IIS_IUSRS ou IUSR (ou à l’utilisateur spécifique associé au pool d’applications) les droits lecture et exécution pour le dossier de l’application Web. Corrigez le problème et redémarrez le pool d’applications.

* Si vous utilisez un fichier HOSTs avec des adresses locales, essayez d’utiliser l’adresse de bouclage à la place de l’adresse IP de l’ordinateur.

* Affichez la page localhost dans le navigateur.

     Si IIS n’est pas installé correctement, vous devez obtenir des erreurs quand vous tapez `http://localhost` dans un navigateur.
     
     Pour plus d’informations sur le déploiement vers IIS, consultez [débogage à distance ASP.net sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou, par ASP.net Core, [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Assurez-vous que la version correcte de ASP.NET est installée sur IIS.  Consultez [déployer une Application ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) ou, par ASP.net Core, la [publication sur IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Créez une application ASP.NET de base sur le serveur.

     Si vous ne pouvez pas faire fonctionner votre application avec le débogueur, essayez de créer une application ASP.NET de base localement sur le serveur et essayez de déboguer l’application de base. Si vous pouvez déboguer une application de base, cela peut vous aider à identifier les différences entre les deux configurations.
  
* Résoudre les erreurs d’authentification si vous utilisez uniquement l’adresse IP

     Par défaut, les adresses IP sont supposées faire partie d'Internet et l'authentification NTLM ne s'effectue pas via Internet. Si votre site Web est configuré dans IIS pour exiger l’authentification, cette authentification échoue. Pour corriger ce problème, vous pouvez spécifier le nom de l’ordinateur distant au lieu de l’adresse IP.
     
## <a name="other-causes"></a>Autres causes

Si vous utilisez une version antérieure de Visual Studio :

- Redémarrez Visual Studio avec des privilèges élevés, puis réessayez.

    Un bogue dans les versions antérieures (corrigé ultérieurement) nécessitait des privilèges élevés dans certains scénarios de débogage ASP.NET.
    
- Si plusieurs instances de Visual Studio sont en cours d’exécution, rouvrez votre projet dans une instance de Visual Studio, puis réessayez.

## <a name="see-also"></a>Voir aussi  
 [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
