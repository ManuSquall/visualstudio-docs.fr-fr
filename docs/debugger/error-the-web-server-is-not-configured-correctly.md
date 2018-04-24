---
title: 'Erreur : Le serveur web n’est pas configuré correctement | Documents Microsoft'
ms.custom: ''
ms.date: 09/20/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9ff79148af491ee27aeae20b66b4d7b742bef6b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Erreur : le serveur web n’est pas configuré correctement

Après avoir suivi les étapes décrites ici pour résoudre le problème et avant de réessayer déboguer, vous devez également réinitialiser IIS. C’est également en ouvrant une invite de commandes administrateur et en tapant `iisreset`.

Ces étapes pour résoudre ce problème :

1. Si l’application web hébergée sur le serveur est configurée comme une version Release, republier comme une version Debug et vérifiez que le fichier web.config contienne `debug=true` dans l’élément de compilation. Réinitialisez IIS, puis réessayez.

    Par exemple, si vous utilisez un profil de publication pour une version Release, remplacez-le par le débogage et republier. Sinon, l’attribut de débogage est fixé à `false` lorsque vous publiez.

2. (IIS) Vérifiez que le chemin d’accès physique est correct. Dans IIS, vous trouverez ce paramètre dans **les paramètres de base > chemin d’accès physique** (ou **paramètres avancés** dans les versions antérieures d’IIS).

    Le chemin d’accès physique peut être incorrect si l’application web a été copiée sur un ordinateur différent, renommée manuellement ou déplacée. Réinitialisez IIS, puis réessayez.

3. Si vous déboguez localement dans Visual Studio, vérifiez que le serveur correct est sélectionné dans les propriétés. (Ouvrez **Propriétés > Web > serveurs** ou **Propriétés > déboguer** en fonction de votre type de projet. Ouvrez un projet Web Forms **Pages de propriétés > Options de démarrage > Server**).

    Si vous utilisez un serveur externe (personnalisé) tels que IIS, l’URL doit être correcte. Sinon, sélectionnez IIS Express, puis réessayez.

4. (IIS) Assurez-vous que la version correcte d’ASP.NET est installée sur le serveur.

    Versions incompatibles de ASP.NET sur IIS et dans votre projet Visual Studio peuvent provoquer ce problème. Vous devrez peut-être définir la version du framework dans le fichier web.config. Pour installer ASP.NET sur IIS, utilisez le [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consultez également [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou, pour ASP.NET Core, [hôte sous Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Si le `maxConnection` limite dans IIS est trop faible et que vous avez trop de connexions, vous devrez peut-être [augmenter la limite de connexion](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Voir aussi  
 [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)