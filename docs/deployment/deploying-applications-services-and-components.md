---
title: Présentation du déploiement
description: Découvrez plus d’informations sur les options de déploiement d’applications à partir de Visual Studio.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8933127940cd8155bbf0854fd19c559022bceecb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912165"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Présentation du déploiement dans Visual Studio

Quand vous déployez une application, un service ou un composant, vous le distribuez pour l’installer sur d’autres ordinateurs, appareils, serveurs ou dans le cloud. Vous choisissez la méthode appropriée dans Visual Studio pour le type de déploiement dont vous avez besoin. (De nombreux types d’applications prennent en charge d’autres outils de déploiement, tels que le déploiement à partir de la ligne de commande ou NuGet, qui ne sont pas décrits ici.)

Consultez les guides de démarrage rapide et les didacticiels pour obtenir des instructions de déploiement pas à pas. Pour une vue d’ensemble des options de déploiement, consultez [Quelles options de publication choisir ?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Déployer sur un dossier local

Le déploiement sur un dossier local est généralement utilisé à des fins de test ou de démarrage d’un déploiement intermédiaire dans lequel un autre outil est utilisé pour le déploiement final.

- **ASP.net**, **ASP.net Core**, **Node.js**, **python** et. **Net Core**: utilisez l’outil de **publication** pour effectuer le déploiement dans un dossier local. Les options disponibles dépendent de votre type d’application. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **Publier**. (Si vous n’avez pas déjà configuré de profil de publication, vous devez sélectionner **créer un nouveau profil**.) Ensuite, sélectionnez **dossier**. Pour plus d’informations, consultez [Déployer dans un dossier local](quickstart-deploy-to-local-folder.md).

    ![Capture d’écran montrant la sélection de publier.](../deployment/media/quickstart-publish.png)

- **Windows Desktop**: vous pouvez publier une application de bureau Windows dans un dossier à l’aide du déploiement ClickOnce. Les utilisateurs peuvent ensuite installer l'application d'un seul clic. Pour plus d’informations, consultez les articles suivants :

  - [Déployez une application de bureau Windows .NET Framework à l’aide de ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md).
  - [Déployez une application de bureau Windows .net à l’aide de ClickOnce](quickstart-deploy-using-clickonce-folder.md).
  - [Déployez une application C++/CLR à l’aide de ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, pour C/C++, consultez [déployer une application native à l’aide d’un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publication dans Azure

- **ASP.net**, **ASP.net Core**, **python** et **Node.js**: publiez sur Azure App service ou Azure App service sur Linux (à l’aide de conteneurs) à l’aide de l’une des méthodes suivantes :

  - Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).
  - Pour un déploiement d’applications ponctuel (ou manuel), utilisez l’outil **Publier** de Visual Studio.

  Pour le déploiement qui fournit une configuration plus personnalisée du serveur, vous pouvez également utiliser l’outil de **publication** pour déployer des applications sur une machine virtuelle Azure.

  Pour utiliser l’outil de **publication** , cliquez avec le bouton droit sur le projet dans Explorateur de solutions et sélectionnez **publier**. (Si vous avez déjà configuré des profils de publication, vous devez sélectionner **créer un nouveau profil**.) Dans la boîte de dialogue **publier** , sélectionnez **app service** ou **machines virtuelles Azure**, puis suivez les étapes de configuration.

  ![Capture d’écran qui montre la sélection de Azure App Service.](../deployment/media/quickstart-publish-azure-new.png "Choisir Azure App Service")

  À compter de Visual Studio 2017 version 15,7, vous pouvez déployer des applications ASP.NET Core pour App Service sur Linux.

  Pour les applications Python, consultez également [Python - Publication sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Pour une présentation rapide, consultez [Publier sur Azure](quickstart-deploy-to-azure.md) et [Publier sur Linux](quickstart-deploy-to-linux.md). Consultez également [Publier une application ASP.NET Core sur Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Pour le déploiement avec Git, consultez [Déploiement continu d’ASP.NET Core sur Azure avec Git](/aspnet/core/publishing/azure-continuous-deployment).

  > [!NOTE]
  > Si vous n’avez pas encore de compte Azure, vous pouvez vous [inscrire ici](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Publiez sur le Web ou déployez-le sur un partage réseau

- **ASP.net**, **ASP.net Core**, **Node.js** et **python**: vous pouvez utiliser l’outil de **publication** pour effectuer un déploiement sur un site Web à l’aide du protocole FTP ou Web Deploy. Pour plus d’informations, consultez [déployer sur un site Web](quickstart-deploy-to-a-web-site.md).

    Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet et sélectionnez **publier**. (Si vous avez déjà configuré des profils de publication, vous devez sélectionner **créer un nouveau profil**.) Dans l’outil de **publication** , sélectionnez l’option souhaitée et suivez les étapes de configuration.

    ![Capture d’écran qui montre la sélection d’IIS.](../deployment/media/quickstart-publish-iis.png)

    Pour plus d’informations sur l’importation d’un profil de publication dans Visual Studio, consultez [Importer des paramètres de publication et déployer sur IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Vous pouvez également déployer des applications et services ASP.NET de plusieurs autres façons. Pour plus d’informations, consultez [Déploiement d’applications et services web ASP.NET](/aspnet/overview/deployment).

- **Windows Desktop**: vous pouvez publier une application de bureau Windows sur un serveur Web ou un partage de fichiers réseau à l’aide du déploiement ClickOnce. Les utilisateurs peuvent ensuite installer l'application d'un seul clic. Pour plus d’informations, consultez les articles suivants :

  - [Déployer une application de bureau Windows .NET Framework à l’aide de ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [Déployer une application de bureau Windows .NET à l’aide de ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [Déployer une application C++/CLR à l’aide de ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Publier sur Microsoft Store

À partir de Visual Studio, vous pouvez créer des packages d’application pour le déploiement sur Microsoft Store.

- **UWP**: vous pouvez empaqueter votre application et la déployer à l’aide d’éléments de menu. Pour plus d’informations, consultez [Empaqueter une application UWP à l’aide de Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Capture d’écran montrant la création d’un package d’application.](../deployment/media/feature-tour-create-app-package.png)

- **Windows Desktop**: vous pouvez effectuer le déploiement sur Microsoft Store à l’aide du pont Desktop à partir de Visual Studio 2017 version 15,4. Pour ce faire, commencez par créer un projet de création de packages d’application Windows. Pour plus d’informations, consultez [Empaqueter une application de bureau pour Microsoft Store (Pont du bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Capture d’écran qui montre la sélection du projet de packaging des applications Windows.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Déployer sur un appareil (UWP)

Si vous déployez une application UWP à des fins de test sur un appareil, consultez [exécuter des applications UWP sur un ordinateur distant dans Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Créer un package d’installation (poste de travail Windows)

Si vous avez besoin d’une installation plus complexe d’une application de bureau que celle que ClickOnce peut fournir, vous pouvez créer un package Windows Installer (fichier d’installation MSI ou EXE) ou un programme d’amorçage personnalisé.

- Vous pouvez créer un package d’installation MSI à l’aide de l' [extension Visual Studio 2017 du jeu d’outils WiX](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Il s’agit d’un ensemble d’outils en ligne de commande.
- Un package d’installation MSI ou EXE peut être créé à l’aide d' [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) à partir du logiciel Flexera. InstallShield peut être utilisé avec Visual Studio 2017 et versions ultérieures. L’édition Community n’est pas prise en charge.

  > [!NOTE]
  > InstallShield Limited Edition n’est plus inclus dans Visual Studio et n’est pas pris en charge dans Visual Studio 2017 et versions ultérieures. Consultez le [logiciel Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) pour connaître la disponibilité future.

- Un package d’installation MSI ou EXE peut être créé à l’aide d’un projet d’installation (vdproj). Pour utiliser cette option, installez l’[extension Projets de Visual Studio Installer](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).
- Vous pouvez aussi installer les composants prérequis pour les applications de poste de travail en configurant un programme d’installation générique, appelé programme d’amorçage. Pour plus d’informations, consultez [Configuration requise](../deployment/application-deployment-prerequisites.md)pour le déploiement d’applications.

## <a name="deploy-to-a-test-lab"></a>Déployer dans un laboratoire de test

Vous pouvez effectuer des développements et des tests plus sophistiqués en déployant vos applications dans des environnements virtuels. Pour plus d'informations, consultez [Tester sur un environnement lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Déploiement continu

Vous pouvez utiliser Azure Pipelines pour permettre le déploiement continu de votre application. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) et [Déployer sur Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>Déployer une base de données SQL

- [Modifier la plateforme cible et publier un projet de base de données (Outils SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Déployer un projet Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Déployer des projets et des packages Integration Services (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Créer et déployer dans une base de données locale](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Déploiement pour d’autres types d’application

| Type d’application | Scénario de déploiement | Lien |
| --- | --- | --- |
| **Application Office** | Vous pouvez publier un complément pour Office à partir de Visual Studio. | [Déployer et publier votre complément Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Service WCF ou OData** | D’autres applications peuvent utiliser des services RIA WCF que vous déployez sur un serveur web. | [Développement et déploiement d’Services de données WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch n’est plus pris en charge à partir de Visual Studio 2017, mais peut encore être déployé à partir de Visual Studio 2015 et versions antérieures. | [Déploiement d’applications LightSwitch](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez eu un bref aperçu des options de déploiement pour différentes applications.

> [!div class="nextstepaction"]
> [Quelles options de publication choisir ?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)