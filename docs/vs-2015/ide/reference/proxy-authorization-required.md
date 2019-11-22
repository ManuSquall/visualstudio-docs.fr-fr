---
title: Autorisation du proxy requise | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297813"
---
# <a name="proxy-authorization-required"></a>Autorisation du proxy requise
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’erreur **autorisation du proxy requise** se produit généralement lorsque les utilisateurs sont connectés aux ressources Visual Studio online via un serveur proxy et que le serveur proxy bloque les appels.

Pour corriger cette erreur, essayez une ou plusieurs des étapes suivantes :

- Redémarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dedans.

- Si l'étape ci-dessus ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d'informations d'identification pour les adresses https://go.microsoft.com, mais uniquement pour les adresses *. visualStudio.com. Pour ces serveurs, vous devez ajouter les URL suivantes à la liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :

  - *.windows.net

  - *.microsoftonline.com

  - *.visualStudio.com

  - *.microsoft.com

  - *.live.com

- Vous pouvez supprimer l’adresse https://go.microsoft.com de la liste verte pour que la boîte de dialogue d’authentification de proxy s’affiche pour l’adresse https://go.microsoft.com et les points de terminaison de serveur lors du redémarrage de Visual Studio.

- Si vous souhaitez utiliser vos informations d’identification par défaut avec votre proxy, procédez comme suit :

   1. Recherchez devenv.exe.config (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (ou **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. Dans le fichier de configuration, recherchez le bloc `<system.net>` , puis et ajoutez le code suivant :

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insérez l’adresse proxy correcte de votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.

- Suivez les instructions de [ce](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) billet de blog pour ajouter du code qui vous permet d’utiliser le proxy.
