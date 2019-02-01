---
title: Autorisation du proxy requise | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b55dba438280fc4579fe15bd2a423d323c38abf6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767279"
---
# <a name="proxy-authorization-required"></a>Autorisation du proxy requise
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Cette erreur se produit généralement lorsque les utilisateurs sont connectés à Visual Studio Online via un serveur proxy et que le serveur proxy bloque les appels. Visual Studio Online est utilisé pour maintenir l'utilisateur connecté à l'IDE.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Redémarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dedans.  
  
-   Si l'étape ci-dessus ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d'informations d'identification pour les adresses http://go.microsoft.com, mais uniquement pour les adresses *. visualStudio.com. Pour ces serveurs, vous devez ajouter les éléments suivants à la liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   Sinon, vous pouvez supprimer le http://go.microsoft.com à partir de la liste blanche d’adresses afin que la boîte de dialogue de l’authentification de proxy s’affiche à la fois pour le http://go.microsoft.com adresse et les points de terminaison de serveur lors du redémarrage de Visual Studio.  
  
-   OU  
  
-   Si vous voulez utiliser vos informations d'identification par défaut avec votre proxy, vous pouvez procéder comme suit :  
  
    1.  Recherchez devenv.exe.config (le fichier de configuration de devenv.exe) dans **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (ou **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2.  Dans le fichier de configuration, recherchez le bloc `<system.net>` , puis et ajoutez le code suivant :  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         Vous devez insérer l'adresse proxy correcte de votre réseau dans `proxyaddress="<http://<yourproxy:port#>`.  
  
-   OU  
  
-   Vous pouvez également suivre les instructions fournies dans [cette publication](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) pour ajouter du code qui vous permettra d’utiliser le proxy.
