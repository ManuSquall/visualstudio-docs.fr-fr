---
title: 'Erreur : Impossible de démarrer le débogage sur le serveur Web | Microsoft Docs'
ms.date: 05/23/2018
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 908500a333303857ac88d27c76b285464913ff1c
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526293"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Erreur : impossible de démarrer le débogage sur le serveur web

Lorsque vous essayez de déboguer une application ASP.NET exécutée sur un serveur Web, vous pouvez obtenir ce message d’erreur : `Unable to start debugging on the Web server`.

Souvent, cette erreur se produit, car une modification de configuration ou d’erreur s’est produite qui nécessite une mise à jour vos Pools d’applications, une réinitialisation d’IIS, ou les deux. Vous pouvez réinitialiser IIS en ouvrant une invite de commandes avec élévation de privilèges et en tapant `iisreset`.

## <a name="specificerrors"></a>Qu’est le message d’erreur détaillé ?

Le `Unable to start debugging on the Web server` message est générique. En règle générale, un message plus spécifique est inclus dans la chaîne d’erreur et qui peuvent vous aider à identifier la cause du problème ou recherchez un correctif plus exact. Voici quelques-uns des messages d’erreur plus courants sont ajoutées au message d’erreur principal :

- [IIS ne répertorie pas un site Web qui correspond au lancement de l’url](#IISlist)
- [Le serveur web n’est pas configuré correctement](#web_server_config)
- [Impossible de se connecter sur le serveur Web](#unabletoconnect)
- [Le serveur web n’a pas répondu en temps voulu](#webservertimeout)
- [Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) ne semble pas s’exécuter sur l’ordinateur distant](#msvsmon)
- [Le serveur distant a retourné une erreur](#server_error)
- [Impossible de démarrer le débogage ASP.NET](#aspnet)
- [Le débogueur ne peut pas se connecter à l’ordinateur distant](#cannot_connect)
- [ Consultez l’aide pour plus d’informations sur les erreurs de configuration courantes. Exécution de la page Web en dehors du débogueur peut fournir davantage d’informations.](#see_help)

## <a name="IISlist"></a> IIS ne répertorie pas un site Web qui correspond au lancement de l’url

- Redémarrez Visual Studio en tant qu’administrateur et recommencez le débogage. (Certains scénarios de débogage ASP.NET nécessitent des privilèges élevés).

    Vous pouvez configurer Visual Studio pour toujours exécuter en tant qu’administrateur en cliquant sur l’icône de raccourci Visual Studio, en choisissant **Propriétés > Avancé**, puis en choisissant de toujours exécuter en tant qu’administrateur.

## <a name="web_server_config"></a> Le serveur web n’est pas configuré correctement

- Consultez [erreur : le serveur web n’est pas configuré correctement](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Impossible de se connecter sur le serveur Web

- Vous êtes en cours d’exécution Visual Studio et le serveur Web sur le même ordinateur et le débogage à l’aide de **F5** (au lieu de **attacher au processus**) ? Ouvrez les propriétés de votre projet et assurez-vous que le projet est configuré pour se connecter au serveur Web approprié et l’URL de lancement. (Ouvrez **Propriétés > Web > serveurs** ou **Propriétés > déboguer** selon votre type de projet. Ouvrez un projet Web Forms **Pages de propriétés > Options de démarrage > serveur**.)

- Sinon, redémarrez votre Pool d’applications et puis réinitialisez IIS. Pour plus d’informations, consultez [Vérifiez votre Configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Le serveur web n’a pas répondu en temps voulu

- Réinitialisez IIS, puis recommencez le débogage. Plusieurs instances du débogueur peuvent être attachés au processus IIS ; une réinitialisation y mette fin. Pour plus d’informations, consultez [Vérifiez votre Configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Microsoft Visual Studio Remote Debugging Monitor (msvsmon.exe) ne semble pas s’exécuter sur l’ordinateur distant.

- Si vous effectuez un débogage sur un ordinateur distant, assurez-vous que vous avez [installé et exécuté le débogueur distant](../debugger/remote-debugging.md). Si le message mentionne un pare-feu, assurez-vous que le [corriger des ports dans le pare-feu](../debugger/remote-debugger-port-assignments.md) sont ouverts, surtout si vous utilisez un pare-feu tiers.
- Si vous utilisez un fichier HOSTS, assurez-vous qu’il est configuré correctement. Par exemple, si le débogage à l’aide **F5** (au lieu de **attacher au processus**), les hôtes de fichiers doit inclure la même URL de projet, comme dans les propriétés de votre projet, **Propriétés > Web > serveurs**  ou **Propriétés > déboguer**, selon votre type de projet.

## <a name="server_error"></a> Le serveur distant a retourné une erreur

Vérifiez votre [fichier journal IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) pour sous-codes d’erreur et des informations supplémentaires et cette IIS 7 [billet de blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

En outre, Voici certains des codes d’erreur courants et quelques suggestions.
- (403) Interdit. Il existe de nombreuses causes possibles pour cette erreur, reportez-vous à votre fichier journal et les paramètres de sécurité IIS pour le site web. Assurez-vous que le fichier web.config du serveur inclut `debug=true` dans l’élément de compilation. Assurez-vous que votre dossier d’Application Web dispose des autorisations appropriées et que votre configuration de Pool d’applications est correcte (un mot de passe a peut-être changé). Consultez [Vérifiez votre Configuration IIS](#vxtbshttpservererrorsthingstocheck). Si ces paramètres sont déjà corrects et que vous déboguez localement, vérifiez également que vous vous connectez sur le type de serveur correct et l’URL (dans **Propriétés > Web > serveurs** ou **Propriétés > déboguer**, selon votre type de projet).
- (503) Serveur non disponible. Le Pool d’applications peut avoir arrêté en raison d’une modification de configuration ou d’erreur. Redémarrez le Pool d’applications.
- (404) Introuvable. Assurez-vous que le Pool d’applications est configuré pour la version correcte d’ASP.NET.

## <a name="aspnet"></a> Impossible de démarrer le débogage ASP.NET

- Redémarrez le Pool d’applications et de réinitialisation de IIS. Pour plus d’informations, consultez [Vérifiez votre Configuration IIS](#vxtbshttpservererrorsthingstocheck).
- Si vous effectuez réécrit les URL, un fichier web.config de base avec aucune URL de réécritures de test. Consultez le **Remarque** relatives à l’URL de réécriture Module dans [Vérifiez votre Configuration IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Le débogueur ne peut pas se connecter à l’ordinateur distant

Si vous effectuez un débogage localement, cette erreur peut se produire, car Visual Studio est une application 32 bits, de sorte qu’il utilise la version 64 bits du débogueur distant pour déboguer des applications 64 bits. Ouvrez les propriétés de votre projet et assurez-vous que le projet est configuré pour se connecter sur le serveur Web et l’URL correcte. (Ouvrez **Propriétés > Web > serveurs** ou **Propriétés > déboguer** selon votre type de projet.)

En outre, si vous utilisez un fichier HOSTS, assurez-vous qu’il est configuré correctement. Par exemple, les hôtes de fichiers doit inclure la même URL de projet, comme dans les propriétés de votre projet, **Propriétés > Web > serveurs** ou **Propriétés > déboguer**, selon votre type de projet.

## <a name="see_help"></a> Consultez l’aide pour plus d’informations sur les erreurs de configuration courantes. Exécution de la page Web en dehors du débogueur peut fournir davantage d’informations.

- Vous exécutez Visual Studio et le serveur Web sur le même ordinateur ? Ouvrez les propriétés de votre projet et assurez-vous que le projet est configuré pour se connecter au serveur Web approprié et l’URL de lancement. (Ouvrez **Propriétés > Web > serveurs** ou **Propriétés > déboguer** selon votre type de projet.)

- Si cela ne fonctionne pas ou si vous effectuez un débogage à distance, suivez les étapes de [Vérifiez votre Configuration IIS](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Vérifiez votre configuration d’IIS

Après avoir pris les mesures décrites ici pour résoudre le problème et avant d’essayer à nouveau de déboguer, vous devrez peut-être également réinitialiser IIS. Vous pouvez le faire en ouvrant une invite de commandes avec élévation de privilèges et en tapant `iisreset`.

* Arrêter et redémarrer vos Pools d’applications IIS, puis réessayez.

    Le Pool d’applications peut avoir arrêté suite à une erreur. Ou bien, une autre modification de configuration que vous avez apportées peut-être nécessiter que vous arrêtez et redémarrez votre Pool d’applications.

    > [!NOTE]
    > Si le Pool d’applications conserve l’arrêt, vous devrez désinstaller le Module de réécriture d’URL à partir du panneau. Vous pouvez réinstaller à l’aide de Web Platform Installer (WebPI). Ce problème peut se produire après une mise à niveau du système significatives.

* Vérifiez votre configuration de Pool d’applications, corrigez-le si nécessaire, puis réessayez.

    Le Pool d’applications peut être configuré pour une version d’ASP.NET qui ne correspond pas à votre projet Visual Studio. Mettre à jour la version d’ASP.NET dans le Pool d’applications et redémarrez-le. Pour plus d’informations, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    En outre, si les informations d’identification de mot de passe ont été modifiés, vous devrez peut-être les mettre à jour dans votre Pool d’applications ou le site Web.  Dans le Pool d’applications, mettre à jour les informations d’identification dans **paramètres avancés > modèle de processus > identité**. Pour le site Web, mettre à jour les informations d’identification dans **paramètres de base > se connecter en tant que...** . Redémarrez votre Pool d’applications.

* Vérifiez que votre dossier d’Application Web dispose des autorisations appropriées.

    Assurez-vous que vous donnez IIS_IUSRS, IUSR, ou associé à l’utilisateur spécifique le [Pool d’applications](/iis/manage/configuring-security/application-pool-identities) lecture et d’exécution des droits pour le dossier d’Application Web. Corrigez le problème et redémarrez votre Pool d’applications.

* Assurez-vous que la version correcte d’ASP.NET est installée sur IIS.

    Versions incompatibles de ASP.NET sur IIS et dans votre projet Visual Studio peuvent provoquer ce problème. Vous devrez peut-être définir la version du framework dans le fichier web.config. Pour installer ASP.NET sur IIS, utilisez le [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). En outre, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou, pour ASP.NET Core, [hôte sur Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Résoudre les erreurs d’authentification si vous utilisez uniquement l’adresse IP

     Par défaut, les adresses IP sont supposées faire partie d'Internet et l'authentification NTLM ne s'effectue pas via Internet. Si votre site web est configuré dans IIS pour exiger l’authentification, cette authentification échoue. Pour corriger ce problème, vous pouvez spécifier le nom de l’ordinateur distant au lieu de l’adresse IP.

## <a name="other-causes"></a>Autres causes

Si la configuration d’IIS n’est pas provoque le problème, essayez les étapes suivantes :

- Redémarrez Visual Studio avec des privilèges d’administrateur et réessayez.

    Certains scénarios de débogage ASP.NET telles que l’utilisation de Web Deploy nécessitent des privilèges élevés pour Visual Studio.

- Si vous exécutent plusieurs instances de Visual Studio, rouvrez votre projet dans une instance de Visual Studio (avec des privilèges d’administrateur), puis réessayez.

- Si vous utilisez un fichier d’hôtes avec les adresses locales, essayez d’utiliser l’adresse de bouclage au lieu de l’adresse IP de l’ordinateur.

    Si vous n’utilisez pas les adresses locales, assurez-vous que votre fichier HOSTS inclut la même URL de projet, comme dans les propriétés de votre projet, **Propriétés > Web > serveurs** ou **Propriétés > déboguer**, selon votre type de projet.

## <a name="more-troubleshooting-steps"></a>Étapes de dépannage supplémentaires

* Afficher la page localhost dans le navigateur sur le serveur.

     Si IIS n’est pas installé correctement, vous devez obtenir des erreurs quand vous tapez `http://localhost` dans un navigateur.

     Pour plus d’informations sur le déploiement vers IIS, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) et, pour ASP.NET Core, [hôte sur Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Créer une application ASP.NET de base sur le serveur (ou utiliser un fichier web.config de base).

    Si vous ne pouvez pas obtenir votre application fonctionne avec le débogueur, essayez de créer une application ASP.NET de base localement sur le serveur et tentez de déboguer l’application de base. (Vous souhaiterez utiliser le modèle ASP.NET MVC par défaut.) Si vous pouvez déboguer une application de base, qui peut vous aider à identifier quelle est la différence entre les deux configurations. Rechercher les différences dans les paramètres dans le fichier web.config, telles que les règles de réécriture d’URL.

## <a name="see-also"></a>Voir aussi
- [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)