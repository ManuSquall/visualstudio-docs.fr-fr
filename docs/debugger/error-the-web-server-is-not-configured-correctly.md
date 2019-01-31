---
title: 'Erreur : Le serveur web n’est pas configuré correctement | Microsoft Docs'
ms.date: 09/20/2017
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd59211da9228f2940c675f889d0536fbea9045d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019190"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Erreur : Le serveur web n’est pas configuré correctement

Après avoir pris les mesures décrites ici pour résoudre le problème et avant d’essayer à nouveau de déboguer, vous devrez peut-être également réinitialiser IIS. Vous pouvez le faire en ouvrant une invite de commandes administrateur et en tapant `iisreset`.

Suivez ces étapes pour résoudre ce problème :

1. Si l’application web hébergée sur le serveur est configurée comme une version Release, republier comme une version Debug et vérifiez que le fichier web.config contienne `debug=true` dans l’élément de compilation. Réinitialisez IIS, puis réessayez.

    Par exemple, si vous utilisez un profil de publication pour une version Release, remplacez-le par le débogage et la republier. Sinon, l’attribut de débogage est fixé à `false` lorsque vous publiez.

2. (IIS) Vérifiez que le chemin d’accès physique est correct. Dans IIS, vous trouverez ce paramètre dans **paramètres de base > chemin d’accès physique** (ou **paramètres avancés** dans les versions antérieures d’IIS).

    Le chemin d’accès physique peut être incorrecte si l’application web a été copiée vers un autre ordinateur, renommée manuellement ou déplacée. Réinitialisez IIS, puis réessayez.

3. Si vous déboguez localement dans Visual Studio, vérifiez que le serveur correct est sélectionné dans les propriétés. (Ouvrez **Propriétés > Web > serveurs** ou **Propriétés > déboguer** selon votre type de projet. Ouvrez un projet Web Forms **Pages de propriétés > Options de démarrage > serveur**).

    Si vous utilisez un serveur externe (personnalisé) tels que IIS, l’URL doit être correcte. Sinon, sélectionnez IIS Express, puis réessayez.

4. (IIS) Assurez-vous que la version correcte d’ASP.NET est installée sur le serveur.

    Versions incompatibles de ASP.NET sur IIS et dans votre projet Visual Studio peuvent provoquer ce problème. Vous devrez peut-être définir la version du framework dans le fichier web.config. Pour installer ASP.NET sur IIS, utilisez le [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). En outre, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou, pour ASP.NET Core, [hôte sur Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Si le `maxConnection` limite dans IIS est trop faible et que vous avez trop de connexions, vous devrez peut-être [augmenter la limite de connexion](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Voir aussi  
 [Débogage distant ASP.NET sur un ordinateur distant IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)