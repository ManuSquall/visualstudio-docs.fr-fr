---
title: "Mise sur liste verte d’URL dans un réseau privé | Microsoft Docs"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a4093c7ebba74493a64833bfbf83ee6d28ef1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="whitelisting-urls-in-a-private-network"></a>Mise sur liste verte d’URL dans un réseau privé

Si vous utilisez Visual Studio dans un réseau privé qui utilise une appliance de sécurité telle qu’un pare-feu, Visual Studio risque de ne pas pouvoir se connecter à certaines ressources réseau. Ces ressources incluent Visual Studio Team Services (VSTS) pour la connexion et la gestion des licences, NuGet et les services Azure. Si Visual Studio ne parvient pas à se connecter à l’une de ces ressources, le message d’erreur suivant s’affiche :

  **La connexion sous-jacente a été fermée : une erreur inattendue s’est produite lors de l’envoi**

Visual Studio utilise le protocole TLS 1.2 pour se connecter aux ressources réseau. Les appliances de sécurité sur certains réseaux privés bloquent certaines connexions serveur quand Visual Studio utilise TLS 1.2. Pour corriger cette erreur, activez les connexions pour les URL suivantes :

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *.azurewebsites.net (pour les connexions Azure)

- *.nuget.org (pour les connexions NuGet)

- *.visualstudio.com

- cdn.vsassets.io (héberge le contenu du réseau de distribution de contenu, ou CDN)

- *.gallerycdn.vsassets.io (héberge les extensions VSTS)

- static2.sharepointonline.com (héberge les ressources que Visual Studio utilise dans le kit d’interface utilisateur de la structure fabric Office, telles que les polices)

> [!NOTE]
> Les URL des serveurs NuGet dont la propriété est privée peuvent ne pas figurer dans la liste ci-dessus. Vous pouvez vérifier les serveurs NuGet que vous utilisez en ouvrant %APPData%\Nuget\NuGet.Config.

## <a name="see-also"></a>Voir aussi

[Erreur d’autorisation du proxy exigée](../ide/reference/proxy-authorization-required.md)  
[Installation de Visual Studio derrière un pare-feu ou un serveur proxy](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
