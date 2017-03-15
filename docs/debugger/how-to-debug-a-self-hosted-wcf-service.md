---
title: "Comment&#160;: d&#233;boguer un service WCF auto-h&#233;berg&#233; | Microsoft Docs"
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
helpviewer_keywords: 
  - "débogage, WCF"
  - "WCF, débogage"
  - "WCF, service auto-hébergé"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: d&#233;boguer un service WCF auto-h&#233;berg&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un *service auto\-hébergé* est un service WCF qui ne s'exécute pas à l'intérieur d'IIS, de l'hôte de service WCF ou du serveur de développement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  La manière la plus facile de déboguer un service WCF auto\-hébergé est de configurer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour lancer à la fois le client et le serveur lorsque vous choisissez **Démarrer le débogage** dans le menu **Déboguer**.  
  
 Si le service WCF est auto\-hébergé dans un processus qui ne peut pas être lancé de cette manière, tel que le service NT, vous ne pouvez pas utiliser cette méthode.  En revanche, vous pouvez effectuer l'une des opérations suivantes :  
  
-   Attachez manuellement le débogueur au processus d'hébergement.  Pour plus d'informations, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     – ou –  
  
-   Commencez à déboguer le client, puis exécutez pas à pas un appel au service.  Cette opération nécessite l'activation du débogage dans le fichier app.config.  Pour plus d'informations, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Pour démarrer à la fois le client et l'hôte à partir de Visual Studio  
  
1.  Créez une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui contient à la fois les projets client et serveur.  
  
2.  Configurez la solution de façon à ce qu'elle démarre à la fois les processus client et serveur lorsque vous choisissez **Démarrer** dans le menu **Déboguer**.  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de la solution.  
  
    2.  Cliquez sur **Définir les projets de démarrage**.  
  
    3.  Dans la boîte de dialogue **Propriétés de la Solution \<Nom\>**, sélectionnez **Plusieurs projets de démarrage**.  
  
    4.  Dans la grille **Plusieurs projets de démarrage**, sur la ligne qui correspond au projet serveur, cliquez sur **Action** et choisissez **Démarrer**.  
  
    5.  Sur la ligne qui correspond au projet client, cliquez sur **Action** et choisissez **Démarrer**.  
  
    6.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Débogage de services WCF](../debugger/debugging-wcf-services.md)   
 [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Comment : effectuer un pas à pas détaillé dans les services WCF](../debugger/how-to-step-into-wcf-services.md)