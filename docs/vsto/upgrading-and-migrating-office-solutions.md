---
title: "La mise à niveau et migration de Solutions Office | Documents Microsoft"
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
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c81cba2c80f8eaabeae15fc5425ed7e02c378123
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="upgrading-and-migrating-office-solutions"></a>Mise à niveau et migration de solutions Office
  Si vous disposez d'un projet Microsoft Office créé dans une version antérieure de Visual Studio, vous devez effectuer une mise à niveau du projet afin de l'utiliser dans la version actuelle de Visual Studio. Pour mettre à niveau un projet Microsoft Office, ouvrez-le dans une version de Visual Studio qui inclut les outils de développement Microsoft Office. Pour plus d’informations sur les versions de Visual Studio qui incluent des outils de développement Microsoft Office, consultez [configuration d’un ordinateur pour développer des Solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
> [!NOTE]  
>  Visual Studio ne peut pas effectuer la mise à niveau des projets de modèle de formulaire InfoPath créés à l'aide de versions antérieures de Visual Studio. Ces types de projets ne sont pas pris en charge dans la version actuelle de Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Modifications apportées aux projets mis à niveau  
 Quand vous mettez à niveau un projet Microsoft Office, Visual Studio modifie le projet pour cibler les éléments suivants :  
  
-   Visual Studio 2010 Tools pour Office Runtime. Pour plus d'informations, consultez [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Références de l'assembly actuel.  
  
-   Version du .NET Framework prise en charge par le type de projet (quand vous effectuez une mise à niveau vers Visual Studio 2013 uniquement).  
  
-   Version de Microsoft Office prise en charge par le type de projet (quand vous effectuez une mise à niveau vers Visual Studio 2013 uniquement).  
  
## <a name="assembly-references"></a>Références d'assembly  
 Visual Studio met à niveau les références d'assembly suivantes dans le projet :  
  
-   Assemblys PIA (Primary Interop Assembly) de Microsoft Office.  
  
-   Assemblys dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Pour plus d’informations sur ces assemblys, consultez [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Nouvelles versions ou versions mises à jour d'assemblys dépendants.  
  
## <a name="targeted-net-framework"></a>.NET Framework ciblé  
 Quand vous mettez à niveau un projet vers Visual Studio 2013, Visual Studio modifie le projet pour cibler [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ou [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La version du .NET Framework ciblée par le projet dépend de la version d'Office installée sur votre ordinateur. Si [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] est installé, Visual Studio modifie le projet pour cibler [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dans le cas contraire, Visual Studio modifie le projet pour cibler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Vous devrez peut-être effectuer quelques étapes supplémentaires pour exécuter une solution reciblée sur les ordinateurs de développement et les ordinateurs des utilisateurs finaux. De plus, votre projet ne pourra plus être compilé s'il utilise certaines fonctionnalités. Pour plus d’informations, consultez [migration de Solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Si vous ciblez [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure dans un projet Office, vous pouvez utiliser certaines fonctionnalités qui ne sont pas disponibles quand vous ciblez .NET Framework 3.5. Pour plus d'informations, consultez [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Application Office ciblée  
 Quand vous mettez à niveau un projet Office vers Visual Studio 2013, Visual Studio modifie le projet pour cibler une version de Microsoft Office qui est prise en charge par le type de projet, tel qu’un projet de personnalisation au niveau du document ou un projet de complément VSTO.  
  
 Les projets Office dans Visual Studio 2013 peuvent cibler les applications [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]  Visual Studio modifie le projet pour cibler la version la plus récente d'Office que vous avez installée. Si aucune de ces versions d'Office n'est installée, Visual Studio ne met pas à niveau le projet.  
  
> [!NOTE]  
>  Si vous mettez à niveau un projet de complément VSTO pour cibler [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou une version ultérieure, assurez-vous que le `ThisAddIn_Startup` Gestionnaire d’événements de la macro complémentaire VSTO ne contient pas le code qui accède à un document dans l’application. Pour plus d'informations, consultez [Accessing a Document When the Office Application Starts](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Pour les personnalisations au niveau du document, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] convertit les documents d'un projet qui ont un format binaire, tels que les documents dotés d'une extension .xls ou .doc, au format Office Open XML. Pour plus d’informations sur Open XML, consultez [Présentation des nouvelles extensions de nom de fichier et des formats Open XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Les balises actives sont déconseillées dans Excel 2010 et Word 2010. Par conséquent, si votre solution utilise des balises actives, vous devez les supprimer pour pouvoir la tester et la déboguer dans Visual Studio 2013 ou Visual Studio 2015.  
  
## <a name="upgrading-microsoft-office-2003-projects"></a>Mise à niveau de projets Microsoft Office 2003  
 D’autres éléments sont à prendre en compte pour la mise à niveau de personnalisations au niveau du document et de compléments VSTO ciblant Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Projets au niveau du document  
 Si le document figurant dans le projet contient des contrôles Windows Forms, Visual Studio 2005 Tools pour Office Second Edition Runtime doit être installé avant la mise à niveau du projet. Si cette version du runtime n'est pas installée sur l'ordinateur de développement avant la mise à niveau du projet, le projet mis à niveau peut contenir des erreurs de compilation ou d'exécution. Une fois la mise à niveau du projet terminée, vous pourrez désinstaller Visual Studio 2005 Tools pour Office Second Edition Runtime de l'ordinateur de développement s'il n'est pas utilisé par d'autres solutions Office. Cette version du runtime est disponible sous forme de package redistribuable dans le Centre de téléchargement Microsoft : [Microsoft Visual Studio 2005 Tools pour Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Projets de complément VSTO  
 Si le fichier solution de votre projet d’origine incluait un projet d’installation ou InstallShield Limited Edition configuré pour installer le complément VSTO, Visual Studio met à niveau du projet, mais il n’apporte aucune autre modification au projet. Si vous voulez continuer à utiliser un fichier Windows Installer pour déployer votre complément VSTO, vous devez modifier le projet d’installation ou InstallShield Limited Edition pour installer les nouveaux composants prérequis tels que [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools pour Office Runtime et éventuellement les assemblys PIA (Primary Interop Assembly) référencés par votre complément VSTO. Pour plus d'informations, consultez [Deploying an Office Solution by Using Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Si vous voulez utiliser ClickOnce pour déployer votre complément VSTO, vous pouvez supprimer entièrement le projet d’installation ou InstallShield Limited Edition. Pour plus d’informations sur le déploiement des Compléments VSTO à l’aide de ClickOnce, consultez [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : mettre à niveau des solutions Office](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)   
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Mise à niveau du projet, boîte de dialogue Options](../vsto/project-upgrade-options-dialog-box.md)  
  
  