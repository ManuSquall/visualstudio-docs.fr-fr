---
title: Résoudre les erreurs réseau ou de proxy
description: Trouvez des solutions aux erreurs réseau ou aux erreurs de proxy que vous pouvez rencontrer quand vous installez ou utilisez Visual Studio derrière un pare-feu ou un serveur proxy.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e7d54b4e7777b3569031e96760699e7c075245f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306824"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Résoudre les erreurs liées au réseau lorsque vous installez ou utilisez Visual Studio

Nous avons des solutions pour résoudre les erreurs liées au réseau ou au proxy les plus fréquemment rencontrées lorsque vous installez ou utilisez Visual Studio derrière un pare-feu ou un serveur proxy.

## <a name="error-proxy-authorization-required"></a>Erreur : « Autorisation du proxy exigée »

Cette erreur se produit généralement quand les utilisateurs sont connectés à Internet via un serveur proxy et que le serveur proxy bloque les appels que Visual Studio effectue vers certaines ressources réseau.

### <a name="to-fix-this-proxy-error"></a>Pour corriger cette erreur de proxy

- Démarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dans la boîte de dialogue lorsque vous y êtes invité.

- Si le redémarrage de Visual Studio ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d’informations d’identification pour les adresses http:&#47;&#47;go.microsoft.com, mais uniquement pour les adresses &#42;.visualStudio.microsoft.com. Pour ces serveurs, envisagez d’ajouter les URL suivantes à une liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Sinon, vous pouvez supprimer l’adresse http:&#47;&#47;go.microsoft.com de la liste verte pour que la boîte de dialogue d’authentification de proxy s’affiche pour l’adresse http:&#47;&#47;go.microsoft.com et pour les points de terminaison de serveur lors du redémarrage de Visual Studio.

  OU

- Si vous voulez utiliser vos informations d'identification par défaut avec votre proxy, vous pouvez procéder comme suit :

::: moniker range="vs-2017"

  1. Recherchez **devenv.exe.config** (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** ou **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Dans le fichier de configuration, recherchez le bloc `<system.net>`, puis ajoutez le code suivant :

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Vous devez insérer l'adresse proxy correcte de votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Pour plus d’informations, consultez les pages [ &lt; &gt; élément defaultProxy (paramètres réseau)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) et [ &lt; &gt; élément proxy (paramètres réseau)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range=">=vs-2019"

  1. Recherchez **devenv.exe.config** (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** ou **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Dans le fichier de configuration, recherchez le bloc `<system.net>`, puis ajoutez le code suivant :

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Vous devez insérer l'adresse proxy correcte de votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Pour plus d’informations, consultez les pages [ &lt; &gt; élément defaultProxy (paramètres réseau)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) et [ &lt; &gt; élément proxy (paramètres réseau)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Erreur : « déconnecté de Visual Studio » lors de la tentative de signalement d’un problème

Cette erreur se produit généralement lorsqu’un utilisateur est connecté à Internet via un serveur proxy et que le serveur proxy bloque les appels que Visual Studio effectue sur certaines ressources réseau.

### <a name="to-fix-this-proxy-error"></a>Pour corriger cette erreur de proxy

1. Recherchez **feedback.exe.config** (le fichier de configuration feedback.exe) dans : **% ProgramFiles (x86)% \ Microsoft Visual Studio\Installer** ou **%ProgramFiles%\Microsoft Visual Studio\Installer**.

2. Dans le fichier de configuration, vérifiez si le code suivant est présent ; Si le code n’est pas présent, ajoutez-le avant la dernière `</configuration>` ligne.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

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

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (héberge le contenu du réseau de distribution de contenu, ou CDN)

- &#42;. gallerycdn.vsassets.io (héberge les extensions d’Azure DevOps Services)

- static2.sharepointonline.com (héberge les ressources que Visual Studio utilise dans le kit Office UI Fabric, telles que les polices)

- &#42;.nuget.org (pour les connexions NuGet)

  > [!NOTE]
  > Les URL des serveurs NuGet dont la propriété est privée peuvent ne pas figurer dans cette liste. Vous pouvez vérifier les serveurs NuGet que vous utilisez dans %APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Erreur : « échec de l’analyse de l’ID du processus parent »

Vous pouvez rencontrer ce message d’erreur lorsque vous utilisez un programme d’amorçage Visual Studio et un response.jssur un lecteur réseau. La source de l’erreur est le contrôle de compte d’utilisateur (UAC) dans Windows.

Voici pourquoi cette erreur peut se produire : un lecteur réseau mappé ou un partage [UNC](/dotnet/standard/io/file-path-formats#unc-paths) est lié au jeton d’accès d’un utilisateur. Lorsque le contrôle de compte d’utilisateur est activé, deux [jetons d’accès](/windows/win32/secauthz/access-tokens) utilisateur sont créés : un *avec* un accès administrateur et un autre *sans* accès administrateur. Lorsqu’un lecteur réseau ou un partage est créé, le jeton d’accès actuel de l’utilisateur est lié à celui-ci. Étant donné que le programme d’amorçage doit être exécuté en tant qu’administrateur, il ne peut pas accéder au lecteur réseau ou au partage si le lecteur ou le partage n’est pas lié à un jeton d’accès utilisateur disposant d’un accès administrateur.

### <a name="to-fix-this-error"></a>Pour corriger cette erreur

Vous pouvez utiliser la `net use` commande ou vous pouvez modifier le paramètre de stratégie de groupe du contrôle de compte d’utilisateur. Pour plus d’informations sur ces solutions de contournement et la façon de les implémenter, consultez les articles du support technique Microsoft suivants :

* [Les lecteurs mappés ne sont pas disponibles à partir d’une invite avec élévation de privilèges lorsque le contrôle de compte d’utilisateur est configuré pour « demander des informations d’identification » dans Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Les programmes peuvent ne pas pouvoir accéder à certains emplacements réseau après l’activation du contrôle de compte d’utilisateur dans les systèmes d’exploitation Windows](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer et utiliser Visual Studio derrière un pare-feu ou un serveur proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Installer Visual Studio](install-visual-studio.md)
