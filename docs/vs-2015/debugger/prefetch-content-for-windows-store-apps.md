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
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300521"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Prérécupérer du contenu pour les applications Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows uniquement] (.. /Image/windows_only_content. png « windows_only_content »)  
  
 Pour que votre application du Windows Store soit plus réactive, vous pouvez demander à Windows de précharger du contenu web, tel que des pages web ou des images, dans le cache [WinINet](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](https://msdn.microsoft.com/library/aa383630.aspx) de l'application. Cette fonctionnalité est appelée prérécupération. Cela est particulièrement efficace pour le contenu utilisé au démarrage mais vous pouvez prérécupérer également d'autre contenu fréquemment utilisé. Les méthodes de la classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) vous permettent de spécifier les URI du contenu à précharger.  
  
 Windows utilise les paramètres heuristiques pour déterminer quand la prérécupération doit avoir lieu et si elle doit avoir lieu, et quelles ressources seront téléchargées. Les paramètres heuristiques prennent en considération le système du réseau et les conditions de puissance, l'historique d'utilisation de l'application par l'utilisateur et les résultats des tentatives des prérécupérations antérieures. Dans Visual Studio, vous pouvez utiliser la commande **Déclencher la prérécupération d’application Windows Store** pour forcer Windows à ignorer les paramètres heuristiques ContentPrefetcher et précharger tout le contenu web spécifié. Cette opération est utile si vous testez le comportement ou les performances de l'application avec le contenu à prérécupérer dans un état connu (chargé ou non chargé).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Pour forcer le préchargement de ressources ContentPrefetcher spécifiées  
 Cette procédure part du principe que vous avez déjà défini la fonctionnalité ContentPrefetcher et spécifié les URI de contenu à précharger dans le projet d'application. Pour forcer un préchargement de contenu lorsque les ressources sont nouvelles ou modifiées, vous devez démarrer et arrêter l’application avant de choisir la commande **Déclencher la prérécupération d’application Windows Store**. Exécutez l'application d'abord pour enregistrer les URI. La commande **Déclencher la prérécupération d’application Windows Store** force alors le ContentPrefetcher à télécharger le contenu et à l’ajouter au cache. Vous pouvez supposer que le contenu est préchargé dans les exécutions suivantes de l'application.  
  
1. Démarrez l'application pour enregistrer les URI de contenu prérécupéré auprès de l'application. Dans le menu **Déboguer**, choisissez **Démarrer le débogage** (raccourci clavier : F5).  
  
2. Dans le menu **Déboguer**, choisissez **Arrêter le débogage** (raccourci clavier : Maj+F5).  
  
3. Dans le menu **Déboguer**, choisissez **Autres cibles de débogage**, puis choisissez **Déclencher la prérécupération d’application Windows Store**.  
  
   Vous pouvez désormais déboguer, tester ou analyser votre application avec des ressources web prérécupérées.  
  
> [!NOTE]
> Répétez ces étapes chaque fois que vous ajoutez ou modifiez du contenu web spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Billet de blog : déclenchement de la prérécupération pour les applications du Windows Store dans Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
