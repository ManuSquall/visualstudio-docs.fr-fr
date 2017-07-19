---
title: Autorisation du proxy requise | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 537928b9ce99cbda9873500780719353d34fcbe1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/14/2017

---
# <a name="proxy-authorization-required"></a>Autorisation du proxy requise
Cette erreur se produit généralement lorsque les utilisateurs sont connectés à Visual Studio Online via un serveur proxy et que le serveur proxy bloque les appels. Visual Studio Online est utilisé pour maintenir l'utilisateur connecté à l'IDE.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Redémarrez Visual Studio. Une boîte de dialogue d'authentification du proxy doit s'afficher. Entrez vos informations d'identification dedans.  
  
-   Si l’étape ci-dessus ne résout pas le problème, cela est peut-être dû au fait que votre serveur proxy ne demande pas d’informations d’identification pour les adresses http://go.microsoft.com, mais uniquement pour les adresses *.visualStudio.com. Pour ces serveurs, vous devez ajouter les éléments suivants à la liste verte pour débloquer tous les scénarios de connexion dans Visual Studio :  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   Sinon, vous pouvez supprimer l’adresse http://go.microsoft.com de la liste verte pour que la boîte de dialogue d’authentification de proxy s’affiche pour l’adresse http://go.microsoft.com et pour les points de terminaison de serveur lors du redémarrage de Visual Studio.  
  
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
