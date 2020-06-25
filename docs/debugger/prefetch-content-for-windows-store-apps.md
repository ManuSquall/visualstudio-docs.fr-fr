---
title: Déboguer à l’aide de contenu de prérécupération dans les applications UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 65b889452a23bb970cbee4c65455679a3473abab
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348065"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Déboguer des applications UWP à l’aide de contenu pré-récupéré dans Visual Studio

 Pour rendre votre application UWP plus réactive, vous pouvez demander à Windows de précharger du contenu Web, tel que des pages Web ou des images, dans le cache [WinInet](/windows/desktop/WinInet/about-wininet) de l’application. Cette fonctionnalité est appelée prérécupération. Ceci est particulièrement efficace pour le contenu utilisé au démarrage mais vous pouvez prérécupérer également d’autres contenus fréquemment utilisés. Les méthodes de la classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) vous permettent de spécifier les URI du contenu à précharger. Consultez l’[exemple de prérécupération de contenu](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) du SDK Windows pour comprendre comment ajouter la fonctionnalité ContentPrefetcher à votre application.

 Windows utilise les paramètres heuristiques pour déterminer quand la prérécupération doit avoir lieu et si elle doit avoir lieu, et quelles ressources seront téléchargées. Les paramètres heuristiques prennent en considération le système du réseau et les conditions de puissance, l'historique d'utilisation de l'application par l'utilisateur et les résultats des tentatives des prérécupérations antérieures. Dans Visual Studio, vous pouvez utiliser la commande **Déclencher la prérécupération d’application Windows Store** pour forcer Windows à ignorer les paramètres heuristiques ContentPrefetcher et précharger tout le contenu web spécifié. Cette opération est utile si vous testez le comportement ou les performances de l'application avec le contenu à prérécupérer dans un état connu (chargé ou non chargé).

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Pour forcer le préchargement de ressources ContentPrefetcher spécifiées
 Cette procédure suppose que la fonctionnalité ContentPrefetcher est déjà définie et que les URI de contenu à précharger sont spécifiés dans le projet d'application. Pour forcer un préchargement de contenu lorsque les ressources sont nouvelles ou modifiées, vous devez démarrer et arrêter l’application avant de choisir la commande **Déclencher la prérécupération d’application Windows Store**. Exécutez l'application d'abord pour enregistrer les URI. La commande **Déclencher la prérécupération d’application Windows Store** force alors le ContentPrefetcher à télécharger le contenu et à l’ajouter au cache. Vous pouvez supposer que le contenu est préchargé dans les exécutions suivantes de l'application.

1. Démarrez l'application pour enregistrer les URI de contenu prérécupéré dans de l'application. Dans le menu **Déboguer**, choisissez **Démarrer le débogage** (raccourci clavier : F5).

2. Dans le menu **Déboguer**, choisissez **Arrêter le débogage** (raccourci clavier : Maj+F5).

3. Dans le menu **Déboguer**, choisissez **Autres cibles de débogage**, puis choisissez **Déclencher la prérécupération d’application Windows Store**.

   Vous pouvez désormais déboguer, tester ou analyser votre application avec des ressources web prérécupérées.

> [!NOTE]
> Répétez ces étapes chaque fois que vous ajoutez ou modifiez du contenu web spécifié.

## <a name="see-also"></a>Voir aussi
- [Billet de blog : déclenchement de la prérécupération pour les applications du Windows Store dans Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)