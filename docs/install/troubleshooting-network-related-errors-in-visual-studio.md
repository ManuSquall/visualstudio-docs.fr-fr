---
title: Résoudre les erreurs réseau ou de proxy
description: Trouvez des solutions aux erreurs réseau ou aux erreurs de proxy que vous pouvez rencontrer quand vous installez ou utilisez Visual Studio derrière un pare-feu ou un serveur proxy.
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4693a50246493a97e74ba75dc7f516ce72a215ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914940"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Résolution des erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio

Nous avons des solutions pour résoudre les erreurs liées au réseau ou au proxy les plus fréquemment rencontrées lorsque vous installez ou utilisez Visual Studio derrière un pare-feu ou un serveur proxy.

## <a name="error-proxy-authorization-required"></a>Erreur : « Autorisation du proxy requise »

Cette erreur se produit généralement quand les utilisateurs sont connectés à Internet via un serveur proxy et que le serveur proxy bloque les appels que Visual Studio effectue vers certaines ressources réseau.

### <a name="to-fix-this-proxy-error"></a>Pour corriger cette erreur de proxy

- Redémarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dans la boîte de dialogue lorsque vous y êtes invité.

- Si le redémarrage de Visual Studio ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d’informations d’identification pour les adresses http:&#47;&#47;go.microsoft.com, mais uniquement pour les adresses &#42;.visualStudio.com. Pour ces serveurs, vous devez ajouter les URL suivantes à la liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- Sinon, vous pouvez supprimer l’adresse http:&#47;&#47;go.microsoft.com de la liste verte pour que la boîte de dialogue d’authentification de proxy s’affiche pour l’adresse http:&#47;&#47;go.microsoft.com et pour les points de terminaison de serveur lors du redémarrage de Visual Studio.

    OU

- Si vous voulez utiliser vos informations d'identification par défaut avec votre proxy, vous pouvez procéder comme suit :

  1. Recherchez **devenv.exe.config** (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** ou **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Dans le fichier de configuration, recherchez le bloc `<system.net>`, puis ajoutez le code suivant :

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#>" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Vous devez insérer l'adresse proxy correcte de votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.

     OU

- Vous pouvez également suivre les instructions fournies dans le billet de blog [Comment se connecter via un proxy Web authentifié](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/), qui vous expliquent comment ajouter du code pour utiliser le proxy.

## <a name="error-the-underlying-connection-was-closed"></a>Erreur : « La connexion sous-jacente a été fermée »

Si vous utilisez Visual Studio dans un réseau privé qui utilise un pare-feu, Visual Studio risque de ne pas pouvoir se connecter à certaines ressources réseau. Ces ressources peuvent inclure Azure DevOps Services pour la connexion et la gestion des licences, NuGet et des services Azure. Si Visual Studio ne parvient pas à se connecter à l’une de ces ressources, le message d’erreur suivant s’affiche :

  **La connexion sous-jacente a été fermée : une erreur inattendue s’est produite lors de l’envoi**

Visual Studio utilise le protocole TLS 1.2 pour se connecter aux ressources réseau. Les appliances de sécurité sur certains réseaux privés bloquent certaines connexions serveur quand Visual Studio utilise TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Pour corriger cette erreur de connexion

Activez les connexions pour les URL suivantes :

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (pour les connexions Azure)

- &#42;.visualstudio.com

- cdn.vsassets.io (héberge le contenu du réseau de distribution de contenu, ou CDN)

- &#42;. gallerycdn.vsassets.io (héberge les extensions d’Azure DevOps Services)

- static2.sharepointonline.com (héberge les ressources que Visual Studio utilise dans le kit Office UI Fabric, telles que les polices)

- &#42;.nuget.org (pour les connexions NuGet)

  > [!NOTE]
  > Les URL des serveurs NuGet dont la propriété est privée peuvent ne pas figurer dans cette liste. Vous pouvez vérifier les serveurs NuGet que vous utilisez dans %APPData%\Nuget\NuGet.Config.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer et utiliser Visual Studio derrière un pare-feu ou un serveur proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Installer Visual Studio 2017](install-visual-studio.md)
