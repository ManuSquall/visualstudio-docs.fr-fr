---
title: "Comment&#160;: rechercher le nom du processus ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "débogage ASP.NET, processus ASP.NET"
  - "processus ASP.NET"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: rechercher le nom du processus ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour créer un attachement à une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en cours d'exécution, vous devez connaître le nom du processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :  
  
-   Si vous exécutez IIS 6.0 ou IIS 7.0, le nom est w3wp.exe.  
  
-   Si vous exécutez une version antérieure d'IIS, le nom est aspnet\_wp.exe.  
  
 Pour les applications construites à l'aide de [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] ou de versions ultérieures, le code [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] peut résider sur le système de fichiers et s'exécuter sous le serveur de test WebDev.WebServer.exe.  Dans ce cas, vous devez créer un attachement à WebDev.WebServer.exe au lieu du processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Ce scénario s'applique uniquement au débogage local.  
  
 Les applications antérieures d'ASP s'exécutent à l'intérieur du processus IIS inetinfo.exe lorsqu'elles s'exécutent in\-process.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour déterminer si le code de projet réside sur le système de fichiers ou IIS  
  
1.  Dans Visual Studio, ouvrez l'**Explorateur de solutions** le cas échéant.  
  
2.  Sélectionnez le nœud supérieur qui contient le nom de l'application.  
  
3.  Si le titre de la fenêtre **Propriétés** contient un chemin d'accès, le code de l'application réside sur le système de fichiers.  
  
     Dans le cas contraire, le titre de la fenêtre **Propriétés** contiendra le nom du site Web.  
  
### Pour déterminer la version d'IIS sous laquelle l'application s'exécute  
  
1.  Recherchez **Outils d'administration** et lancez\-le.  Selon votre système d'exploitation, il peut s'agir d'une icône à l'intérieur du **Panneau de configuration** ou d'une entrée de menu qui apparaît lorsque vous cliquez sur **Démarrer**.  
  
     Dans Windows XP, le **Panneau de configuration** peut être en affichage des catégories ou en affichage classique.  En affichage des catégories, vous devez cliquer sur **Basculer vers l'affichage classique** ou **Performances et maintenance** pour voir l'icône **Outils d'administration**.  
  
2.  Dans les **Outils d'administration**, exécutez Services Internet \(IIS\).  Une boîte de dialogue MMC apparaît.  
  
3.  Si plusieurs ordinateurs sont répertoriés dans le volet gauche, sélectionnez celui sur lequel réside le code de l'application.  
  
4.  La version d'IIS se trouve dans la colonne **Version** du volet droit.  
  
## Voir aussi  
 [Conditions requises pour le débogage à distance d'applications Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Configuration requise](../debugger/aspnet-debugging-system-requirements.md)   
 [Préparation d'un débogage ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Débogage d'applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)