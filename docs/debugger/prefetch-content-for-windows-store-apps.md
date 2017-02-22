---
title: "Pr&#233;r&#233;cup&#233;rer du contenu pour les applications Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Pr&#233;r&#233;cup&#233;rer du contenu pour les applications Windows Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour que votre application Windows Store soit plus réactive, vous pouvez demander à Windows de précharger du contenu web, comme des pages web ou des images, dans le cache [WinINet](http://msdn.microsoft.com/fr-fr/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx) votre application. Cette fonctionnalité est appelée prérécupération. Cela est particulièrement efficace pour le contenu utilisé au démarrage mais vous pouvez prérécupérer également d'autre contenu fréquemment utilisé. Les méthodes de la classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) vous permettent de spécifier les URI du contenu que vous voulez précharger. Consultez l'[exemple de prérécupération de contenu](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) du SDK Windows pour comprendre comment ajouter la fonctionnalité ContentPrefetcher à votre application.  
  
 Windows utilise les paramètres heuristiques pour déterminer quand la prérécupération doit avoir lieu et si elle doit avoir lieu, et quelles ressources seront téléchargées. Les paramètres heuristiques prennent en considération le système du réseau et les conditions de puissance, l'historique d'utilisation de l'application par l'utilisateur et les résultats des tentatives des prérécupérations antérieures. Dans Visual Studio, vous pouvez utiliser la commande **Déclencher la prérécupération d'application Windows Store** pour forcer Windows à ignorer les paramètres heuristiques ContentPrefetcher et précharger tout le contenu web spécifié. Cette opération est utile si vous testez le comportement ou les performances de l'application avec le contenu à prérécupérer dans un état connu \(chargé ou non chargé\).  
  
## Pour forcer le préchargement de ressources ContentPrefetcher spécifiées  
 Cette procédure part du principe que vous avez déjà défini la fonctionnalité ContentPrefetcher et spécifié les URI de contenu à précharger dans le projet d'application. Pour forcer un préchargement de contenu lorsque les ressources sont nouvelles ou modifiées, vous devez démarrer et arrêter l'application avant de choisir la commande **Déclencher la prérécupération d'application Windows Store**. Exécutez l'application d'abord pour enregistrer les URI. La commande **Déclencher la prérécupération d'application Windows Store** force alors le ContentPrefetcher à télécharger le contenu et à l'ajouter au cache. Vous pouvez supposer que le contenu est préchargé dans les exécutions suivantes de l'application.  
  
1.  Démarrez l'application pour enregistrer les URI de contenu prérécupéré auprès de l'application. Dans le menu **Déboguer**, choisissez **Démarrer le débogage** \(Raccourci clavier : F5\).  
  
2.  Dans le menu **Déboguer**, choisissez **Arrêter le débogage** \(Raccourci clavier : Maj\+F5\).  
  
3.  Dans le menu **Déboguer**, choisissez **Autres cibles de débogage**, puis **Déclencher la prérécupération d'application Windows Store**.  
  
 Vous pouvez désormais déboguer, tester ou analyser votre application avec des ressources web prérécupérées.  
  
> [!NOTE]
>  Répétez ces étapes chaque fois que vous ajoutez ou modifiez le contenu web spécifié.  
  
## Voir aussi  
 [Billet de blog : Triggering Prefetch for Windows Store Apps in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)