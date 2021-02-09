---
title: Impossible de démarrer le débogage sur le serveur Web | Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94dcfdc05f2d852e1a433067b0a574444632195d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870881"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Erreur : impossible de démarrer le débogage sur le serveur web

Lorsque vous essayez de déboguer une application ASP.NET qui s’exécute sur un serveur Web, vous pouvez obtenir ce message d’erreur : `Unable to start debugging on the Web server` .

Cette erreur se produit souvent en raison d’une erreur ou d’une modification de configuration nécessitant une mise à jour de vos pools d’applications, d’une réinitialisation d’IIS ou des deux. Vous pouvez réinitialiser IIS en ouvrant une invite de commandes avec élévation de privilèges et en tapant `iisreset` .

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Quel est le message d’erreur détaillé ?

Le `Unable to start debugging on the Web server` message est générique. En règle générale, un message plus spécifique est inclus dans la chaîne d’erreur et peut vous aider à identifier la cause du problème ou à rechercher un correctif plus exact. Voici quelques-uns des messages d’erreur les plus courants qui sont ajoutés au message d’erreur principal :

- [IIS ne répertorie pas un site Web qui correspond à l’URL de lancement](#IISlist)
- [Le serveur web n’est pas configuré correctement](#web_server_config)
- [Impossible de se connecter au serveur webserver](#unabletoconnect)
- [Le serveur Web n’a pas répondu dans le délai imparti](#webservertimeout)
- [Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) ne semble pas s’exécuter sur l’ordinateur distant](#msvsmon)
- [Le serveur distant a retourné une erreur](#server_error)
- [Impossible de démarrer le débogage ASP.NET](#aspnet)
- [Le débogueur ne peut pas se connecter à l’ordinateur distant](#cannot_connect)
- [Consultez l'aide pour plus d'informations sur les erreurs de configuration usuelles. Exécution de la page Web en dehors du débogueur peut fournir davantage d’informations.](#see_help)
- [Opération non prise en charge. Erreur inconnue : *errornumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS ne répertorie pas un site Web qui correspond à l’URL de lancement

- Redémarrez Visual Studio en tant qu’administrateur et recommencez le débogage. (Certains scénarios de débogage de ASP.NET requièrent des privilèges élevés.)

    Vous pouvez configurer Visual Studio pour qu’il s’exécute toujours en tant qu’administrateur en cliquant avec le bouton droit sur l’icône de raccourci de Visual Studio, en sélectionnant **propriétés > avancé**, puis en sélectionnant toujours exécuter en tant qu’administrateur.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Le serveur Web n’est pas configuré correctement

- [Erreur : le serveur Web n’est pas configuré correctement](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Impossible de se connecter au serveur webserver

- Exécutez-vous Visual Studio et le serveur Web sur le même ordinateur et déboguez-les à l’aide de la touche **F5** (au lieu de **attacher au processus**) ? Ouvrez les propriétés de votre projet et assurez-vous que le projet est configuré pour se connecter au serveur Web et au lancement de l’URL appropriés. (Ouvrez les **propriétés > serveurs** ou propriétés du > Web **> déboguer** en fonction du type de votre projet. Pour un projet Web Forms, ouvrez **pages de propriétés > options de démarrage > serveur**.)

- Dans le cas contraire, redémarrez votre pool d’applications, puis réinitialisez IIS. Pour plus d’informations, consultez [vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Le serveur Web n’a pas répondu dans le délai imparti

- Réinitialisez IIS et recommencez le débogage. Plusieurs instances de débogueur peuvent être attachées au processus IIS ; une réinitialisation les termine. Pour plus d’informations, consultez [vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Le moniteur de débogage distant Microsoft Visual Studio (msvsmon.exe) ne semble pas être en cours d’exécution sur l’ordinateur distant

- Si vous effectuez un débogage sur un ordinateur distant, assurez-vous que vous avez [installé et que vous exécutez le débogueur distant](../debugger/remote-debugging.md). Si le message mentionne un pare-feu, assurez-vous que les [ports appropriés dans le pare-feu](../debugger/remote-debugger-port-assignments.md) sont ouverts, en particulier si vous utilisez un pare-feu tiers.
- Si vous utilisez un fichier HOSTs, assurez-vous qu’il est correctement configuré. Par exemple, si vous déboguez à l’aide de la touche **F5** (au lieu de **attacher au processus**), le fichier hosts doit inclure la même URL de projet que dans les propriétés de votre projet, **Propriétés > serveurs** ou propriétés du > Web **> déboguer**, selon le type de projet.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Le serveur distant a retourné une erreur

Consultez votre [fichier journal IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) pour en savoir plus sur les codes d’erreur et obtenir des informations supplémentaires, et ce billet de [blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)IIS 7.

En outre, voici quelques-uns des codes d’erreur courants et quelques suggestions.
- (403) Interdit. Il existe de nombreuses causes possibles pour cette erreur. Vérifiez donc votre fichier journal et les paramètres de sécurité IIS pour le site Web. Assurez-vous que le web.config du serveur comprend `debug=true` dans l’élément compilation. Assurez-vous que le dossier de votre application Web dispose des autorisations appropriées et que la configuration de votre pool d’applications est correcte (un mot de passe a peut-être été modifié). Consultez [vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck). Si ces paramètres sont déjà corrects et que vous déboguez localement, vérifiez également que vous vous connectez au type de serveur et à l’URL corrects (dans **propriétés > serveurs Web >** ou **Propriétés > déboguer**, en fonction de votre type de projet).
- (503) Serveur non disponible. Le pool d’applications a peut-être été arrêté en raison d’une erreur ou d’une modification de la configuration. Redémarrez le pool d’applications.
- (404) Introuvable. Assurez-vous que le pool d’applications est configuré pour la version correcte de ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a> Impossible de démarrer le débogage ASP.NET

- Redémarrez le pool d’applications et réinitialisez IIS. Pour plus d’informations, consultez [vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck).
- Si vous effectuez une réécriture d’URL, testez un web.config de base sans réécriture d’URL. Consultez la **Remarque** sur le module de réécriture d’URL dans [vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Le débogueur ne peut pas se connecter à l’ordinateur distant

Si vous déboguez localement, ouvrez les propriétés de votre projet dans Visual Studio et assurez-vous que le projet est configuré pour se connecter au serveur Web et à l’URL appropriés. (Ouvrez les **propriétés > serveurs** ou propriétés du > Web **> déboguer** en fonction de votre type de projet.)

Cette erreur peut se produire lors du débogage local, car Visual Studio est une application 32 bits. elle utilise donc la version 64 bits du débogueur distant pour déboguer des applications 64 bits. Vérifiez votre pool d’applications sur IIS pour vous assurer que l’option **activer les applications 32 bits** est définie sur `true` , Redémarrez IIS, puis réessayez.

En outre, si vous utilisez un fichier HOSTs, assurez-vous qu’il est correctement configuré. Par exemple, le fichier HOSTs doit inclure l’URL du projet comme dans les propriétés de votre projet, les **propriétés > les serveurs** ou les propriétés du > Web **> Debug**, en fonction de votre type de projet.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Consultez l’aide pour les erreurs de configuration courantes. L’exécution de la page Web en dehors du débogueur peut fournir des informations supplémentaires.

- Exécutez-vous Visual Studio et le serveur Web sur le même ordinateur ? Ouvrez les propriétés de votre projet et assurez-vous que le projet est configuré pour se connecter au serveur Web et au lancement de l’URL appropriés. (Ouvrez les **propriétés > serveurs** ou propriétés du > Web **> déboguer** en fonction de votre type de projet.)

- Si cela ne fonctionne pas ou si vous effectuez un débogage à distance, suivez les étapes de [la section vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> Opération non prise en charge. Erreur inconnue : *errornumber*

Si vous effectuez une réécriture d’URL, testez un web.config de base sans réécriture d’URL. Consultez la **Remarque** sur le module de réécriture d’URL dans [vérifier votre configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Vérifier la configuration d’IIS

Après avoir pris les mesures décrites ici pour résoudre le problème, et avant de réessayer de déboguer, vous devrez peut-être également réinitialiser IIS. Pour ce faire, ouvrez une invite de commandes avec élévation de privilèges et tapez `iisreset` .

* Arrêtez et redémarrez vos pools d’applications IIS, puis réessayez.

    Le pool d’applications a peut-être été arrêté suite à une erreur. Ou, une autre modification de configuration que vous avez apportée peut nécessiter l’arrêt et le redémarrage de votre pool d’applications.

    > [!NOTE]
    > Si le pool d’applications continue à s’arrêter, vous devrez peut-être désinstaller le module de réécriture d’URL à partir du panneau de configuration. Vous pouvez le réinstaller à l’aide de l’Web Platform Installer (WebPI). Ce problème peut se produire après une mise à niveau importante du système.

* Vérifiez la configuration de votre pool d’applications, corrigez-la si nécessaire, puis réessayez.

    Le pool d’applications peut être configuré pour une version de ASP.NET qui ne correspond pas à votre projet Visual Studio. Mettez à jour la version de ASP.NET dans le pool d’applications et redémarrez-la. Pour plus d’informations, consultez [IIS 8,0 avec ASP.NET 3,5 et ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    En outre, si les informations d’identification du mot de passe ont changé, vous devrez peut-être les mettre à jour dans votre pool d’applications ou site Web.  Dans le pool d’applications, mettez à jour les informations d’identification dans **Paramètres avancés > modèle de processus > identité**. Pour le site Web, mettez à jour les informations d’identification dans **paramètres de base > se connecter en tant que...**. Redémarrez votre pool d’applications.

* Vérifiez que le dossier de votre application Web dispose des autorisations appropriées.

    Veillez à donner à IIS_IUSRS, IUSR ou à l’utilisateur spécifique associé aux droits lecture et exécution du [pool d’applications](/iis/manage/configuring-security/application-pool-identities) pour le dossier de l’application Web. Corrigez le problème et redémarrez le pool d’applications.

* Assurez-vous que la version correcte de ASP.NET est installée sur IIS.

    Les versions incompatibles de ASP.NET sur IIS et dans votre projet Visual Studio peuvent entraîner ce problème. Vous devrez peut-être définir la version du Framework dans web.config. Pour installer ASP.NET sur IIS, utilisez la [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consultez également [iis 8,0 avec ASP.NET 3,5 et ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou, pour ASP.net Core, [héberger sur Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Résoudre les erreurs d’authentification si vous utilisez uniquement l’adresse IP

     Par défaut, les adresses IP sont supposées faire partie d'Internet et l'authentification NTLM ne s'effectue pas via Internet. Si votre site Web est configuré dans IIS pour exiger l’authentification, cette authentification échoue. Pour corriger ce problème, vous pouvez spécifier le nom de l’ordinateur distant au lieu de l’adresse IP.

## <a name="other-causes"></a>Autres causes

Si la configuration IIS n’est pas à l’origine du problème, procédez comme suit :

- Redémarrez Visual Studio avec des privilèges d’administrateur, puis réessayez.

    Certains scénarios de débogage ASP.NET, tels que l’utilisation de Web Deploy requièrent des privilèges élevés pour Visual Studio.

- Si plusieurs instances de Visual Studio sont en cours d’exécution, rouvrez votre projet dans une instance de Visual Studio (avec des privilèges d’administrateur), puis réessayez.

- Si vous utilisez un fichier HOSTs avec des adresses locales, essayez d’utiliser l’adresse de bouclage à la place de l’adresse IP de l’ordinateur.

    Si vous n’utilisez pas d’adresses locales, assurez-vous que votre fichier HOSTs contient la même URL que celle des propriétés de votre projet, ainsi que les **propriétés > serveurs** ou propriétés du > Web **> déboguer**, en fonction de votre type de projet.

## <a name="more-troubleshooting-steps"></a>Autres étapes de dépannage

* Affichez la page localhost dans le navigateur sur le serveur.

     Si IIS n’est pas installé correctement, vous devez obtenir des erreurs quand vous tapez `http://localhost` dans un navigateur.

     Pour plus d’informations sur le déploiement vers IIS, consultez [iis 8,0 à l’aide de ASP.NET 3,5 et ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) et, pour ASP.net Core, [héberger sur Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Créez une application ASP.NET de base sur le serveur (ou utilisez un fichier de web.config de base).

    Si vous ne pouvez pas faire fonctionner votre application avec le débogueur, essayez de créer une application ASP.NET de base localement sur le serveur et essayez de déboguer l’application de base. (Vous pouvez utiliser le modèle ASP.NET MVC par défaut.) Si vous pouvez déboguer une application de base, cela peut vous aider à identifier les différences entre les deux configurations. Recherchez les différences de paramètres dans le fichier web.config, telles que les règles de réécriture d’URL.

## <a name="see-also"></a>Voir aussi
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)