---
title: Prérécupérer du contenu pour les applications du Windows Store | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9329cad2f0125288aeea146070188d023d1a126
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211443"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Prérécupérer du contenu pour les applications Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique uniquement à Windows] (.. /Image/windows_only_content.png « windows_only_content »)  
  
 Pour rendre votre application Windows Store plus réactive, vous pouvez demander à Windows de précharger du contenu web, comme des pages web ou des images, dans l’application [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)cache. Cette fonctionnalité est appelée prérécupération. Cela est particulièrement efficace pour le contenu utilisé au démarrage mais vous pouvez prérécupérer également d'autre contenu fréquemment utilisé. Les méthodes de la [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) classe vous permettre de spécifier l’URI du contenu que vous voulez précharger. Consultez le kit SDK Windows [exemple de prérécupération de contenu](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) pour obtenir des exemples montrant comment ajouter la fonctionnalité ContentPrefetcher à votre application.  
  
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



