---
title: "Correction des erreurs d’autorisation du proxy requise | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e33e0e2896ccb3a5f7fe6d6da57f509af30d77fe
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="proxy-authorization-required"></a>Autorisation du proxy requise

Cette erreur se produit généralement quand les utilisateurs sont connectés à Internet via un serveur proxy et que le serveur proxy bloque les appels que Visual Studio effectue vers certaines ressources réseau.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Redémarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dedans.

- Si l’étape ci-dessus ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d’informations d’identification pour les adresses http://go.microsoft.com, mais uniquement pour les adresses *.visualStudio.com. Pour ces serveurs, vous devez ajouter les URL suivantes à la liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- Sinon, vous pouvez supprimer l’adresse http://go.microsoft.com de la liste verte pour que la boîte de dialogue d’authentification de proxy s’affiche pour l’adresse http://go.microsoft.com et pour les points de terminaison de serveur lors du redémarrage de Visual Studio.

    OU

- Si vous voulez utiliser vos informations d'identification par défaut avec votre proxy, vous pouvez procéder comme suit :

    1. Recherchez **devenv.exe.config** (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** ou **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. Dans le fichier de configuration, recherchez le bloc `<system.net>` , puis et ajoutez le code suivant :

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Vous devez insérer l'adresse proxy correcte de votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.

    OU

- Vous pouvez également suivre les instructions fournies dans [cette publication](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) pour ajouter du code qui vous permettra d’utiliser le proxy.
