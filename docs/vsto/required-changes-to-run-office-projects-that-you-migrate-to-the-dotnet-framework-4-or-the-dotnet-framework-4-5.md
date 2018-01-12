---
title: "Pour exécuter des projets Office que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5 modification nécessaire | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ee90d5c205f58736f7ccb6536e29b2fd6d16b152
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Modifications requises pour exécuter des projets Office qui font l'objet d'une migration vers .NET Framework 4 ou .NET Framework 4.5
  Si l’infrastructure cible d’un projet Office est remplacée par la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure à partir d’une version antérieure du .NET Framework, vous devez effectuer les tâches suivantes pour vous assurer que la solution puisse s’exécuter sur l’ordinateur de développement et sur les ordinateurs des utilisateurs finaux :  
  
-   Supprimez l'élément <xref:System.Security.SecurityTransparentAttribute> du projet si vous avez effectué une mise à niveau à partir de Visual Studio 2008.  
  
-   Effectuer un **Clean** dans Visual Studio pour pouvoir exécuter ou déboguer le projet sur l’ordinateur de développement.  
  
-   Mettez à jour le composant requis .NET Framework du projet.  
  
-   Les utilisateurs finaux doivent également réinstaller la solution si vous l'avez précédemment déployée à l'aide de ClickOnce avant d'avoir changé la version cible de .NET Framework.  
  
 Pour plus d'informations sur chacune de ces tâches, consultez les sections correspondantes ci-dessous.  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Suppression de l'attribut SecurityTransparent dans les projets mis à niveau à partir de Visual Studio 2008  
 Si vous mettez à niveau un projet Office à partir de Visual Studio 2008 et que la version cible de .Net Framework du projet est ensuite remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez supprimer <xref:System.Security.SecurityTransparentAttribute> du projet. Visual Studio ne supprime pas automatiquement cet attribut. Si vous ne supprimez pas cet attribut, un message d'erreur s'affiche lorsque vous compilez le projet.  
  
 Pour plus d’informations sur les conditions dans lesquelles Visual Studio peut modifier l’infrastructure cible d’un projet mis à niveau vers la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consultez [mise à niveau et migration de Solutions Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Pour supprimer l'attribut SecurityTransparentAttribute  
  
1.  Le projet étant ouvert dans Visual Studio, ouvrez l' **Explorateur de solutions**.  
  
2.  Sous le nœud **Propriétés** (pour C#) ou le nœud **My Project** (pour Visual Basic), double-cliquez sur le fichier de code AssemblyInfo pour l'ouvrir dans l'éditeur de code.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, vous devez cliquer sur le bouton **Afficher tous les fichiers** de l' **Explorateur de solutions** pour afficher le fichier de code AssemblyInfo.  
  
3.  Localisez l'élément <xref:System.Security.SecurityTransparentAttribute>, puis supprimez-le du fichier ou commentez-le.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Exécution de la commande Clean pour déboguer ou exécuter un projet sur l'ordinateur de développement  
 Si un projet Office a été créé avant la modification du framework cible du projet pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez effectuer un **Clean** commande, puis régénérez le projet après la modification du framework cible. Si n’effectuent pas un **Clean** de commande, vous recevrez un <xref:System.Runtime.InteropServices.COMException> lorsque vous essayez de déboguer ou exécuter le projet reciblé.  
  
 Pour plus d’informations sur la **Clean** command, consultez [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
## <a name="updating-the-prerequisites-for-deployment"></a>Mise à jour des composants requis pour le déploiement  
 Lorsque vous reciblez un projet Office vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez également mettre à jour les composants requis .NET Framework correspondants dans le **conditions préalables** boîte de dialogue. Sinon, le déploiement ClickOnce ou le projet InstallShield Limited Edition recherche et installe une version antérieure du .NET Framework.  
  
 Pour plus d’informations sur la mise à jour de la configuration requise pour le déploiement pour les ordinateurs des utilisateurs finaux, consultez [Comment : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des Solutions Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>Réinstallation de solutions sur les ordinateurs des utilisateurs finaux  
 Si vous utilisez ClickOnce pour déployer une solution Office qui cible .NET Framework 3.5, puis que vous reciblez le projet vers [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, les utilisateurs finaux doivent désinstaller la solution puis la réinstaller une fois que vous l'avez republiée. Si vous republiez la solution reciblée et si la solution est mise à jour sur les ordinateurs des utilisateurs finaux, les utilisateurs finaux reçoivent une <xref:System.Runtime.InteropServices.COMException> lorsqu'ils exécutent la solution mise à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Migration de solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  