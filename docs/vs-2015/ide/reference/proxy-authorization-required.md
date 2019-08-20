---
title: Autorisation du proxy requise | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822067"
---
# <a name="proxy-authorization-required"></a>Autorisation du proxy requise
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le **autorisation du Proxy requise** erreur se produit généralement lorsque les utilisateurs sont connectés aux ressources en ligne de Visual Studio via un serveur proxy et le serveur proxy bloque les appels.

Pour corriger cette erreur, essayez une ou plusieurs des étapes suivantes :

- Redémarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dedans.

- Si l'étape ci-dessus ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d'informations d'identification pour les adresses http://go.microsoft.com, mais uniquement pour les adresses *. visualStudio.com. Pour ces serveurs, vous devez ajouter les URL suivantes à la liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :

  - \* .windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Vous pouvez supprimer le http://go.microsoft.com à partir de la liste verte d’adresses afin que la boîte de dialogue de l’authentification de proxy s’affiche à la fois pour le http://go.microsoft.com adresse et les points de terminaison de serveur lors du redémarrage de Visual Studio.

- Si vous souhaitez utiliser vos informations d’identification par défaut avec votre proxy, procédez comme suit :

   1. Recherchez devenv.exe.config (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (ou **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Dans le fichier de configuration, recherchez le bloc `<system.net>` , puis et ajoutez le code suivant :

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insérer l’adresse proxy correcte pour votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.

- Suivez les instructions de [ce billet de blog](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) pour ajouter du code qui vous permet d’utiliser le proxy.
