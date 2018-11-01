---
title: Mettre à niveau et migrer des solutions Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b86699f11ab59aaf0ef09f5c7ae52d69e41e96c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671740"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Mettre à niveau et migrer des solutions Office
  Si vous disposez d'un projet Microsoft Office créé dans une version antérieure de Visual Studio, vous devez effectuer une mise à niveau du projet afin de l'utiliser dans la version actuelle de Visual Studio. Pour mettre à niveau un projet Microsoft Office, ouvrez-le dans une version de Visual Studio qui inclut les outils de développement Microsoft Office. Pour plus d’informations sur les versions de Visual Studio qui incluent les outils de développement Microsoft Office, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.  
  
> [!NOTE]  
>  Visual Studio ne peut pas effectuer la mise à niveau des projets de modèle de formulaire InfoPath créés à l'aide de versions antérieures de Visual Studio. Ces types de projets ne sont pas pris en charge dans la version actuelle de Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Modifications apportées aux projets mis à niveau  
 Quand vous mettez à niveau un projet Microsoft Office, Visual Studio modifie le projet pour cibler les éléments suivants :  
  
-   Visual Studio 2010 Tools pour Office runtime. Pour plus d’informations, consultez [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Références de l'assembly actuel.  
  
-   Version du .NET Framework prise en charge par le type de projet (quand vous effectuez une mise à niveau vers Visual Studio 2013 uniquement).  
  
-   Version de Microsoft Office prise en charge par le type de projet (quand vous effectuez une mise à niveau vers Visual Studio 2013 uniquement).  
  
## <a name="assembly-references"></a>Références d’assembly  
 Visual Studio met à niveau les références d'assembly suivantes dans le projet :  
  
-   Assemblys PIA (Primary Interop Assembly) de Microsoft Office.  
  
-   Assemblys dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Pour plus d’informations sur ces assemblys, consultez [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Nouvelles versions ou versions mises à jour d'assemblys dépendants.  
  
## <a name="targeted-net-framework"></a>.NET Framework ciblé  
 Quand vous mettez à niveau un projet vers Visual Studio 2013, Visual Studio modifie le projet pour cibler [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ou [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La version du .NET Framework ciblée par le projet dépend de la version d'Office installée sur votre ordinateur. Si [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] est installé, Visual Studio modifie le projet pour cibler [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dans le cas contraire, Visual Studio modifie le projet pour cibler [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Vous devrez peut-être effectuer quelques étapes supplémentaires pour exécuter une solution reciblée sur les ordinateurs de développement et les ordinateurs des utilisateurs finaux. De plus, votre projet ne pourra plus être compilé s'il utilise certaines fonctionnalités. Pour plus d’informations, consultez [solutions Office de migrer vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Si vous ciblez [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure dans un projet Office, vous pouvez utiliser certaines fonctionnalités qui ne sont pas disponibles quand vous ciblez .NET Framework 3.5. Pour plus d’informations, consultez [conception et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Application Office ciblée  
 Quand vous mettez à niveau un projet Office vers Visual Studio 2013, Visual Studio modifie le projet pour cibler une version de Microsoft Office qui est prise en charge par le type de projet, tel qu’un projet de personnalisation au niveau du document ou un projet de complément VSTO.  
  
 Les projets Office dans Visual Studio 2013 peuvent cibler les applications [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]  Visual Studio modifie le projet pour cibler la version la plus récente d'Office que vous avez installée. Si aucune de ces versions d'Office n'est installée, Visual Studio ne met pas à niveau le projet.  
  
> [!NOTE]  
>  Si vous mettez à niveau un projet de complément VSTO pour cibler [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou version ultérieure, assurez-vous que le `ThisAddIn_Startup` Gestionnaire d’événements de la macro complémentaire VSTO ne contient pas le code qui accède à un document dans l’application. Pour plus d’informations, consultez [accéder à un document lorsque l’application Office démarre](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Pour les personnalisations au niveau du document, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] convertit les documents dans un projet qui ont un format binaire, tels que les documents qui ont une *.xls* ou *.doc* extension, au format Office Open XML. Pour plus d’informations sur Open XML, consultez [Introduction aux nouvelles extensions de nom de fichier et Open XML formats](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Les balises actives sont déconseillées dans Excel 2010 et Word 2010. Par conséquent, si votre solution utilise des balises actives, vous devez les supprimer pour pouvoir la tester et la déboguer dans Visual Studio 2013 ou Visual Studio 2015.  
  
## <a name="upgrade-microsoft-office-2003-projects"></a>Mettre à niveau les projets Microsoft Office 2003  
 D’autres éléments sont à prendre en compte pour la mise à niveau de personnalisations au niveau du document et de compléments VSTO ciblant Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Projets au niveau du document  
 Si le document figurant dans le projet contient des contrôles Windows Forms, Visual Studio 2005 Tools pour Office Second Edition Runtime doit être installé avant la mise à niveau du projet. Si cette version du runtime n'est pas installée sur l'ordinateur de développement avant la mise à niveau du projet, le projet mis à niveau peut contenir des erreurs de compilation ou d'exécution. Une fois la mise à niveau du projet terminée, vous pourrez désinstaller Visual Studio 2005 Tools pour Office Second Edition Runtime de l'ordinateur de développement s'il n'est pas utilisé par d'autres solutions Office. Cette version du runtime est disponible sous forme de package redistribuable dans le Centre de téléchargement Microsoft : [Microsoft Visual Studio 2005 Tools pour Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Projets de complément VSTO  
 Si le fichier solution de votre projet d’origine incluait un projet d’installation ou InstallShield Limited Edition configuré pour installer le complément VSTO, Visual Studio met à niveau du projet, mais il n’apporte aucune autre modification au projet. Si vous voulez continuer à utiliser un fichier Windows Installer pour déployer votre complément VSTO, vous devez modifier le projet d’installation ou InstallShield Limited Edition pour installer les nouveaux composants prérequis tels que [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools pour Office Runtime et éventuellement les assemblys PIA (Primary Interop Assembly) référencés par votre complément VSTO. Pour plus d’informations, consultez [déployer une solution Office à l’aide du programme d’installation de Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Si vous voulez utiliser ClickOnce pour déployer votre complément VSTO, vous pouvez supprimer entièrement le projet d’installation ou InstallShield Limited Edition. Pour plus d’informations sur le déploiement de compléments VSTO à l’aide de ClickOnce, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : solutions de mise à niveau d’Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)   
 [Migrer des solutions Office vers .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Mise à niveau, boîte de dialogue Options projets](../vsto/project-upgrade-options-dialog-box.md)  
  
  