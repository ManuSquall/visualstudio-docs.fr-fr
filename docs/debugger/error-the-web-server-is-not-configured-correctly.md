---
description: Après avoir pris les mesures décrites ici pour résoudre le problème, et avant de réessayer de déboguer, vous devrez peut-être également réinitialiser IIS.
title: Le serveur Web n’est pas correctement configuré | Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82af476e51e8fe016e5966847c8c6a7b3e45b0ce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146520"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Erreur : le serveur Web n'est pas configuré correctement

Après avoir pris les mesures décrites ici pour résoudre le problème, et avant de réessayer de déboguer, vous devrez peut-être également réinitialiser IIS. Pour ce faire, ouvrez une invite de commandes d’administrateur et tapez `iisreset` .

Pour résoudre ce problème, procédez comme suit :

1. Si l’application Web hébergée sur le serveur est configurée en tant que version Release, republiez en tant que version Debug et vérifiez que le fichier web.config contient `debug=true` dans l’élément compilation. Réinitialisez IIS et réessayez.

    Par exemple, si vous utilisez un profil de publication pour une version Release, remplacez-le par déboguer et republier. Dans le cas contraire, l’attribut de débogage est défini sur lors de la `false` publication.

2. INFORMATION Vérifiez que le chemin d’accès physique est correct. Dans IIS, vous trouvez ce paramètre dans **paramètres de base > chemin d’accès physique** (ou **Paramètres avancés** dans les versions antérieures d’IIS).

    Le chemin d’accès physique peut être incorrect si l’application Web a été copiée sur un ordinateur différent, renommée manuellement ou déplacée. Réinitialisez IIS et réessayez.

3. Si vous effectuez un débogage local dans Visual Studio, vérifiez que le serveur correct est sélectionné dans les propriétés. (Ouvrez les **propriétés > serveurs** ou propriétés du > Web **> déboguer** en fonction du type de votre projet. Pour un projet Web Forms, ouvrez **pages de propriétés > options de démarrage > serveur**).

    Si vous utilisez un serveur externe (personnalisé) comme IIS, l’URL doit être correcte. Dans le cas contraire, sélectionnez IIS Express et réessayez.

4. INFORMATION Assurez-vous que la version correcte de ASP.NET est installée sur le serveur.

    Les versions incompatibles de ASP.NET sur IIS et dans votre projet Visual Studio peuvent entraîner ce problème. Vous devrez peut-être définir la version du Framework dans web.config. Pour installer ASP.NET sur IIS, utilisez la [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consultez également [iis 8,0 avec ASP.NET 3,5 et ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou, pour ASP.net Core, [héberger sur Windows avec IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Si la `maxConnection` limite dans IIS est trop faible et que vous avez trop de connexions, vous devrez peut-être [augmenter la limite de connexion](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Voir aussi
- [Débogage distant ASP.NET sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
