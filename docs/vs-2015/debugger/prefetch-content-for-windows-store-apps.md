---
title: Prérécupérer du contenu pour les applications du Windows Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b7d8b859efa5fac2e3643f4d3a0bd694cd2edd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948688"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Prérécupérer du contenu pour les applications Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique uniquement à Windows] (.. /Image/windows_only_content.png « windows_only_content »)  
  
 Pour rendre votre application Windows Store plus réactive, vous pouvez demander à Windows de précharger du contenu web, comme des pages web ou des images, dans l’application [WinINet](http://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)cache. Cette fonctionnalité est appelée prérécupération. Cela est particulièrement efficace pour le contenu utilisé au démarrage mais vous pouvez prérécupérer également d'autre contenu fréquemment utilisé. Les méthodes de la classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) vous permettent de spécifier les URI du contenu à précharger. Consultez l’[exemple de prérécupération de contenu](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) du SDK Windows pour comprendre comment ajouter la fonctionnalité ContentPrefetcher à votre application.  
  
 Windows utilise les paramètres heuristiques pour déterminer quand la prérécupération doit avoir lieu et si elle doit avoir lieu, et quelles ressources seront téléchargées. Les paramètres heuristiques prennent en considération le système du réseau et les conditions de puissance, l'historique d'utilisation de l'application par l'utilisateur et les résultats des tentatives des prérécupérations antérieures. Dans Visual Studio, vous pouvez utiliser la commande **Déclencher la prérécupération d’application Windows Store** pour forcer Windows à ignorer les paramètres heuristiques ContentPrefetcher et précharger tout le contenu web spécifié. Cette opération est utile si vous testez le comportement ou les performances de l'application avec le contenu à prérécupérer dans un état connu (chargé ou non chargé).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Pour forcer le préchargement de ressources ContentPrefetcher spécifiées  
 Cette procédure suppose que la fonctionnalité ContentPrefetcher est déjà définie et que les URI de contenu à précharger sont spécifiés dans le projet d'application. Pour forcer un préchargement de contenu lorsque les ressources sont nouvelles ou modifiées, vous devez démarrer et arrêter l’application avant de choisir la commande **Déclencher la prérécupération d’application Windows Store**. Exécutez l'application d'abord pour enregistrer les URI. La commande **Déclencher la prérécupération d’application Windows Store** force alors le ContentPrefetcher à télécharger le contenu et à l’ajouter au cache. Vous pouvez supposer que le contenu est préchargé dans les exécutions suivantes de l'application.  
  
1. Démarrez l'application pour enregistrer les URI de contenu prérécupéré dans de l'application. Dans le menu **Déboguer**, choisissez **Démarrer le débogage** (Raccourci clavier : F5).  
  
2. Sur le **déboguer** menu, choisissez **arrêter le débogage** (raccourci clavier : MAJ + F5).  
  
3. Dans le menu **Déboguer**, choisissez **Autres cibles de débogage**, puis choisissez **Déclencher la prérécupération d’application Windows Store**.  
  
   Vous pouvez désormais déboguer, tester ou analyser votre application avec des ressources web prérécupérées.  
  
> [!NOTE]
>  Répétez ces étapes chaque fois que vous ajoutez ou modifiez du contenu web spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Billet de blog : Déclencher la prérécupération pour les applications du Windows Store dans Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)
