---
title: "Comment&#160;: installer Visual Studio Tools pour Office Runtime Redistributable"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "installer des outils de développement Office dans Visual Studio"
  - "Office Runtime (développement Office dans Visual Studio)"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# Comment&#160;: installer Visual Studio Tools pour Office Runtime Redistributable
  Visual Studio 2010 Tools pour Office Runtime doit être installé sur chaque ordinateur qui exécute des solutions créées à l'aide des Outils de développement Microsoft Office dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Le runtime est installé automatiquement quand vous installez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et Microsoft Office.  Pour plus d'informations, consultez [Scénarios d'installation de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Dans les situations suivantes, vous devrez peut\-être suivre les instructions d'installation manuelles ci\-dessous :  
  
-   Vous devez installer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sur un serveur.  Par exemple, vous souhaitez utiliser la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour gérer des solutions au niveau du document sur un serveur.  
  
-   Vous devez installer le runtime sur un ordinateur sur lequel tous les autres composants requis pour les solutions Office sont déjà installés.  
  
    > [!NOTE]  
    >  Vous devez être administrateur de l'ordinateur de développement pour installer le .NET Framework et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
### Pour installer Visual Studio Tools pour Office Runtime  
  
1.  Installez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure.  
  
    -   Pour télécharger le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consultez [Microsoft .NET Framework 4 \(programme d'installation web\)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Pour télécharger le [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consultez [Microsoft .NET Framework 4 Client Profile \(programme d'installation web\)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Pour télécharger le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consultez [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Exécutez vstor\_redist.exe pour installer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Vous pouvez télécharger ces fichiers d'installation à partir de [Visual Studio 2010 Tools pour Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384).  Les composants requis pour [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondent aux composants requis du .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclut des modules linguistiques.  Si votre installation de Windows est définie avec une autre langue que l'anglais, vous pouvez afficher les messages du runtime dans la même langue que celle de Windows.  De même, si les utilisateurs finaux installent [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et qu'ils exécutent ensuite vos solutions sur des installations Windows définies avec une autre langue que l'anglais, les messages du runtime apparaîtront dans la même langue que celle de Windows.  Dans certains cas, vous pouvez avoir besoin de modules linguistiques supplémentaires.  Cela peut arriver si, par exemple, si votre version de Windows utilise plusieurs paramètres de langue ou que vous basculez vers une autre langue après avoir déjà installé [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Pour obtenir d'autres modules linguistiques, consultez [Module linguistique Microsoft Visual Studio 2010 Tools pour Microsoft Office System \(runtime version 4.0\)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## Voir aussi  
 [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configuration d'un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Comment configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Comment : installer les assemblys PIA &#40;Primary Interop Assembly&#41; d'Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Gestion de documents sur un serveur à l'aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)  
  
  