---
title: "Modifications requises pour ex&#233;cuter des projets Office qui font l&#39;objet d&#39;une migration vers .NET Framework 4 ou .NET Framework 4.5 | Microsoft Docs"
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
  - "projets Office (développement Office dans Visual Studio), migrer vers .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Modifications requises pour ex&#233;cuter des projets Office qui font l&#39;objet d&#39;une migration vers .NET Framework 4 ou .NET Framework 4.5
  Si la version cible de .Net Framework d'un projet Office devient [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure du .NET Framework en remplacement d'une version antérieure du .NET Framework, vous devez effectuer les tâches suivantes pour garantir que la solution puisse s'exécuter sur l'ordinateur de développement et sur les ordinateurs des utilisateurs finaux :  
  
-   Supprimez l'élément <xref:System.Security.SecurityTransparentAttribute> du projet si vous avez effectué une mise à niveau à partir de Visual Studio 2008.  
  
-   Exécutez une commande **Clean** dans Visual Studio pour pouvoir exécuter ou déboguer le projet sur l'ordinateur de développement.  
  
-   Mettez à jour le composant requis .NET Framework du projet.  
  
-   Les utilisateurs finaux doivent également réinstaller la solution si vous l'avez précédemment déployée à l'aide de ClickOnce avant d'avoir changé la version cible de .NET Framework.  
  
 Pour plus d'informations sur chacune de ces tâches, consultez les sections correspondantes ci\-dessous.  
  
## Suppression de l'attribut SecurityTransparent dans les projets mis à niveau à partir de Visual Studio 2008  
 Si vous mettez à niveau un projet Office à partir de Visual Studio 2008 et que la version cible de .Net Framework du projet est ensuite remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez supprimer <xref:System.Security.SecurityTransparentAttribute> du projet. Visual Studio ne supprime pas automatiquement cet attribut. Si vous ne supprimez pas cet attribut, un message d'erreur s'affiche lorsque vous compilez le projet.  
  
 Pour plus d'informations sur les conditions dans lesquelles Visual Studio peut modifier la version cible de .Net Framework d'un projet mis à niveau vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consultez [Mise à niveau et migration de solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### Pour supprimer l'attribut SecurityTransparentAttribute  
  
1.  Avec le projet ouvert dans Visual Studio, ouvrez l'**Explorateur de solutions**.  
  
2.  Sous le nœud **Propriétés** \(pour C\#\) ou le nœud **My Project** \(pour Visual Basic\), double\-cliquez sur le fichier de code AssemblyInfo pour l'ouvrir dans l'éditeur de code.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, vous devez cliquer sur le bouton **Afficher tous les fichiers** de l'**Explorateur de solutions** pour afficher le fichier de code AssemblyInfo.  
  
3.  Localisez l'élément <xref:System.Security.SecurityTransparentAttribute>, puis supprimez\-le du fichier ou commentez\-le.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## Exécution de la commande Clean pour déboguer ou exécuter un projet sur l'ordinateur de développement  
 Si un projet Office a été généré avant que la version cible de .Net Framework du projet devienne [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez exécuter une commande **Clean**, puis régénérer le projet après le changement de version cible de .Net Framework.  Si vous n'exécutez pas une commande **Clean**, une <xref:System.Runtime.InteropServices.COMException> est levée quand vous essayez de déboguer ou d'exécuter le projet reciblé.  
  
 Pour plus d'informations sur la commande **Clean**, consultez [Génération de solutions Office](../vsto/building-office-solutions.md).  
  
## Mise à jour des composants requis pour le déploiement  
 Lorsque vous reciblez un projet Office vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez également mettre à jour le composant requis .NET Framework correspondants dans la boîte de dialogue **Composants requis**.  Sinon, le déploiement ClickOnce ou le projet InstallShield Limited Edition recherche et installe une version antérieure du .NET Framework.  
  
 Pour plus d'informations sur la mise à jour des composants requis pour le déploiement sur les ordinateurs des utilisateurs finaux, consultez [Comment : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](http://msdn.microsoft.com/fr-fr/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## Réinstallation de solutions sur les ordinateurs des utilisateurs finaux  
 Si vous utilisez ClickOnce pour déployer une solution Office qui cible .NET Framework 3.5, puis que vous reciblez le projet vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, les utilisateurs finaux doivent désinstaller la solution puis la réinstaller une fois que vous l'avez republiée.  Si vous republiez la solution reciblée et si la solution est mise à jour sur les ordinateurs des utilisateurs finaux, les utilisateurs finaux reçoivent une <xref:System.Runtime.InteropServices.COMException> lorsqu'ils exécutent la solution mise à jour.  
  
## Voir aussi  
 [Migration de solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  