---
title: Déboguer à l’aide d’un contenu prérécupéré dans les applications UWP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 458b320b971cbb3c4db74d6f2202455332ca5465
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056320"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Déboguer des applications UWP à l’aide d’un contenu prérécupéré dans Visual Studio
  
 Pour rendre votre application UWP plus réactive, vous pouvez demander à Windows de précharger du contenu web, comme des pages web ou des images, dans l’application [WinINet](/windows/desktop/WinInet/about-wininet) cache. Cette fonctionnalité est appelée prérécupération. Il est particulièrement efficace pour le contenu qui est utilisé au démarrage, mais vous pouvez Prérécupérer autre contenu fréquemment utilisé, trop. Les méthodes de la [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) classe vous permettre de spécifier l’URI du contenu que vous voulez précharger. Consultez le kit SDK Windows [exemple de prérécupération de contenu](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) pour obtenir des exemples montrant comment ajouter la fonctionnalité ContentPrefetcher à votre application.  
  
 Windows utilise les paramètres heuristiques pour déterminer quand la prérécupération doit avoir lieu et si elle doit avoir lieu, et quelles ressources seront téléchargées. Les paramètres heuristiques prennent en considération le système du réseau et les conditions de puissance, l'historique d'utilisation de l'application par l'utilisateur et les résultats des tentatives des prérécupérations antérieures. Dans Visual Studio, vous pouvez utiliser la **déclencher la prérécupération d’application Windows Store** commande pour forcer Windows à ignorer les paramètres heuristiques ContentPrefetcher et précharger tout le contenu web spécifié. Cette opération est utile si vous testez le comportement ou les performances de l'application avec le contenu à prérécupérer dans un état connu (chargé ou non chargé).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Pour forcer le préchargement de ressources ContentPrefetcher spécifiées  
 Cette procédure suppose que la fonctionnalité ContentPrefetcher est déjà définie et que les URI de contenu à précharger sont spécifiés dans le projet d'application. Pour forcer un préchargement de contenu lorsque les ressources spécifiées sont nouveaux ou modifiés, vous devez démarrer et arrêter l’application avant de choisir le **déclencher la prérécupération d’application Windows Store** commande. Exécutez l'application d'abord pour enregistrer les URI. **Déclencher la prérécupération d’application Windows Store** commande force alors le ContentPrefetcher à télécharger le contenu et l’ajouter au cache. Vous pouvez supposer que le contenu est préchargé dans les exécutions suivantes de l'application.  
  
1.  Démarrez l'application pour enregistrer les URI de contenu prérécupéré dans de l'application. Sur le **déboguer** menu, choisissez **démarrer le débogage** (raccourci clavier : F5).  
  
2.  Sur le **déboguer** menu, choisissez **arrêter le débogage** (raccourci clavier : MAJ + F5).  
  
3.  Sur le **déboguer** menu, choisissez **autres cibles de débogage** , puis **déclencher la prérécupération d’application Windows Store**.  
  
 Vous pouvez désormais déboguer, tester ou analyser votre application avec des ressources web prérécupérées.  
  
> [!NOTE]
>  Répétez ces étapes chaque fois que vous ajoutez ou modifiez du contenu web spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Billet de blog : déclencher la prérécupération pour Windows Store les applications dans Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)