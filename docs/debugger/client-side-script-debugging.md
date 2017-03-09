---
title: "D&#233;bogage de scripts c&#244;t&#233; client | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "débogage [Visual Studio], scripts côté client"
  - "scripts côté client, débogage"
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage de scripts c&#244;t&#233; client
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogueur Visual Studio fournit un environnement de débogage complet pour rechercher et corriger les erreurs dans les scripts clients des pages ASP.NET.  
  
## Ouverture de documents de script  
 Vous pouvez afficher des listes de documents de script côté serveur et côté client dans l’**Explorateur de solutions**. Vous pouvez ouvrir tout document de script à partir de l'**Explorateur de solutions**. Pour plus d'informations, consultez [Comment : afficher les documents de script](../debugger/how-to-view-script-documents.md).  
  
## Mappage de point d'arrêt  
 Dans Visual Studio, vous ne pouvez pas déboguer directement le code côté serveur, mais vous pouvez définir un point d'arrêt dans un fichier côté serveur. Visual Studio mappe automatiquement le point d'arrêt à un emplacement correspondant dans le fichier côté client et crée un point d'arrêt mappé dans le code côté client.  
  
## Attachement manuel ou automatique au script  
 Pour commencer le débogage du script dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], le débogueur doit effectuer l'attachement au script que vous souhaitez déboguer. Cela peut se faire manuellement ou automatiquement.  
  
 Vous pouvez effectuer l'attachement manuellement à l'aide de l'interface de débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour choisir un processus de script en cours d'exécution auquel effectuer l'attachement. Pour plus d'informations, consultez [Comment : attacher à un script](../debugger/how-to-attach-to-script.md).  
  
 Le débogueur effectue l'attachement au script automatiquement lorsque l'un des cas suivants se produit :  
  
-   Vous avez atteint un jeu de points d'arrêt dans le script.  
  
-   Vous avez atteint une instruction `Stop` VBScript ou une instruction `debugger` JScript dans votre code de script.  
  
-   Le navigateur ou le serveur rencontre une erreur de syntaxe ou d'exécution dans votre script. Lorsque cela se produit, une boîte de dialogue apparaît et propose de commencer le débogage.  
  
 Lorsque vous effectuez l'attachement au script manuellement, le processus de script continue de s'exécuter jusqu'à ce qu'il soit interrompu d'une manière ou d'une autre. Vous pouvez l'arrêter en sélectionnant **Arrêter** dans le menu **Débogage**.  
  
 Lorsque le débogueur effectue l'attachement automatiquement, l'exécution du script est interrompue à la ligne où le point d'arrêt, l'instruction `Stop` ou `debugger` ou l'erreur s'est produit\(e\), ou au point où vous avez choisi de lancer le débogage dans Internet Explorer.  
  
 À ce stade, vous pouvez utiliser les fonctions normales de débogage pour commencer le débogage. Par exemple, vous pouvez utiliser les commandes **Step** pour continuer à exécuter votre code ligne par ligne. Vous pouvez utiliser la fenêtre **Pile des appels** pour afficher et contrôler le flux de script. Vous pouvez utiliser les fenêtres de variables ou la fenêtre **Immédiat** pour afficher ou modifier des variables et des propriétés.  
  
## Amélioration des messages d'erreur liés au débogage des scripts  
 Visual Studio fournit des messages d’erreur améliorés pour les problèmes courants de débogage de scripts. Ces messages n'apparaissent pas, à moins que vous n'effectuiez l'attachement manuellement à Internet Explorer. Si vous rencontrez une condition d'erreur lorsqu'Internet Explorer est ouvert automatiquement, essayez d'effectuer l'attachement manuellement afin de voir les messages d'erreur.  
  
## Débogage d'applications de script AJAX  
 Les applications Web AJAX ont un usage intensif du code de script et représentent un sérieux défi pour le débogage. Pour plus d'informations sur les techniques de débogage AJAX, consultez  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md).  
  
## Voir aussi  
 [Débogage d'applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitations du débogage de script](../debugger/limitations-on-script-debugging.md)   
 [Fenêtres de variables](../Topic/Variable%20Windows.md)   
 [Fenêtre Exécution](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)