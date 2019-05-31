---
title: Présentation des fonctionnalités de déploiement
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae70551fdb223856774f7e2afa0d85f915f27a0c
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261982"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Présentation du déploiement dans Visual Studio

Quand vous déployez une application, un service ou un composant, vous le distribuez pour l’installer sur d’autres ordinateurs, appareils, serveurs ou dans le cloud. Vous choisissez la méthode appropriée dans Visual Studio pour le type de déploiement dont vous avez besoin. (De nombreux types d’application prennent en charge d’autres outils de déploiement comme l’outil de déploiement en ligne de commande ou NuGet qui ne sont pas décrits ici.)

Consultez les guides de démarrage rapide et les tutoriels pour obtenir des instructions de déploiement pas à pas. Pour une vue d’ensemble des options de déploiement, consultez [Quelles options de publication choisir ?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Déployer dans un dossier local

Le déploiement dans un dossier local est généralement utilisé pour les tests ou pour lancer un déploiement de préproduction dans lequel un autre outil est utilisé pour le déploiement final.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** et.** NET Core** : utilisez l’outil Publier pour effectuer le déploiement dans un dossier local. Les options disponibles dépendent de votre type d’application. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et choisissez **Publier**. (Si vous n’avez pas encore configuré de profils de publication, vous devez cliquer sur **Créer un profil**.) Ensuite, choisissez **Dossier**. Pour plus d’informations, consultez [Déployer dans un dossier local](quickstart-deploy-to-local-folder.md).

    ![Choisir Publier](../deployment/media/quickstart-publish.png)

- **Windows Desktop** : vous pouvez publier une application Windows Desktop sur un dossier avec un déploiement ClickOnce. Les utilisateurs peuvent ensuite installer l'application d'un seul clic. Pour plus d’informations, consultez [Déployer une application de poste de travail avec ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# et Visual Basic). Pour C++/ CLR, consultez [Déployer une application native avec ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, pour C/C++, consultez [Déployer une application native avec un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publier sur Azure

- **ASP.NET**, **ASP.NET Core**, **Python** et **Node.js** : Publiez sur Azure App Service ou Azure App Service Linux (avec des conteneurs) en utilisant une des méthodes suivantes.

  - Pour le déploiement continu (ou automatisé) d’applications, utilisez Azure DevOps avec [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

  - Pour un déploiement d’applications ponctuel (ou manuel), utilisez l’outil **Publier** de Visual Studio.

  Pour un déploiement qui permet une configuration plus personnalisée du serveur, vous pouvez aussi utiliser l’outil **Publier** pour déployer des applications sur une machine virtuelle Azure.

  Pour utiliser l’outil **Publier**, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions et choisissez **Publier**. (Si vous avez déjà configuré des profils de publication, vous devez cliquer sur **Créer un profil**.) Dans la boîte de dialogue Publier, choisissez **App Service** ou **Machines virtuelles Azure**, puis suivez les étapes de configuration.

  ![Choisir Azure App Service](../deployment/media/quickstart-publish-azure.png "Choisir Azure App Service")

  À compter de Visual Studio 2017 version 15.7, vous pouvez déployer des applications ASP.NET Core sur **App Service pour Linux**.

  Pour les applications Python, consultez également [Python - Publication sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Pour une présentation rapide, consultez [Publier sur Azure](quickstart-deploy-to-azure.md) et [Publier sur Linux](quickstart-deploy-to-linux.md). Consultez également [Publier une application ASP.NET Core sur Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Pour le déploiement avec Git, consultez [Déploiement continu d’ASP.NET Core sur Azure avec Git](/aspnet/core/publishing/azure-continuous-deployment).

  Pour plus d’informations sur l’importation d’un profil de publication à partir d’Azure App Service vers Visual Studio, consultez [Importer des paramètres de publication et déployer sur Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Si vous n’avez pas encore de compte Azure, vous pouvez vous [inscrire ici](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publier sur le web ou déployer sur un partage réseau

- **ASP.NET**, **ASP.NET Core**, **Node.js** et **Python** : vous pouvez utiliser l’outil Publier pour effectuer un déploiement sur un site web à l’aide de FTP ou de Web Deploy. Pour plus d’informations, consultez [Déployer sur un site web](quickstart-deploy-to-a-web-site.md).

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**. (Si vous avez déjà configuré des profils de publication, vous devez cliquer sur **Créer un profil**.) Dans l’outil Publier, choisissez l’option souhaitée et suivez les étapes de configuration.

    ![Choisissez IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Pour plus d’informations sur l’importation d’un profil de publication dans Visual Studio, consultez [Importer des paramètres de publication et déployer sur IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Vous pouvez également déployer des applications et services ASP.NET de plusieurs autres façons. Pour plus d’informations, consultez [Déploiement d’applications et services web ASP.NET](http://www.asp.net/aspnet/overview/deployment).

- **Windows Desktop** : Vous pouvez publier une application Windows Desktop sur un serveur web ou un partage de fichiers réseau à l’aide du déploiement ClickOnce. Les utilisateurs peuvent ensuite installer l'application d'un seul clic. Pour plus d’informations, consultez [Déployer une application de poste de travail avec ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# et Visual Basic). Pour C++/ CLR, consultez [Déployer une application native avec ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, pour C/C++, consultez [Déployer une application native avec un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Publier sur Microsoft Store

À partir de Visual Studio, vous pouvez créer des packages d’application pour le déploiement sur Microsoft Store.

- **UWP** : vous pouvez empaqueter votre application et la déployer à l’aide des éléments de menu. Pour plus d’informations, consultez [Empaqueter une application UWP à l’aide de Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Créer un package d'application](../deployment/media/feature-tour-create-app-package.jpg)

- **Bureau Windows** : vous pouvez effectuer un déploiement sur Microsoft Store à l’aide du Pont du bureau à partir de la version 15.4 de Visual Studio 2017. Pour ce faire, commencez par créer un projet de création de packages d’application Windows. Pour plus d’informations, consultez [Empaqueter une application de bureau pour Microsoft Store (Pont du bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Pont du bureau](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Déployer sur un appareil (UWP)

Si vous déployez une application UWP à des fins de test sur un appareil, consultez [Exécuter des applications UWP sur un ordinateur distant dans Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Créer un package d’installation (poste de travail Windows)

Si vous avez besoin d’une installation pour une application de poste de travail plus complexe que ce que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) peut fournir, vous pouvez créer un package Windows Installer (fichier d’installation MSI ou EXE) ou un programme d’amorçage personnalisé.

- Vous pouvez créer un package d’installation MSI avec [l’extension WiX Toolset de Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Il s’agit d’un ensemble d’outils en ligne de commande.

- Vous pouvez créer un package d’installation MSI ou EXE avec [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) de Flexera Software. Vous pouvez utiliser InstallShield avec Visual Studio 2017 et versions ultérieures (l’édition Community n’est pas prise en charge). Notez qu’InstallShield Limited Edition n’est plus inclus avec Visual Studio et n’est pas pris en charge dans Visual Studio 2017 et versions ultérieures. Vérifiez auprès de [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) la disponibilité future.

- Vous pouvez créer un package d’installation MSI ou EXE en utilisant un projet d’installation (vdproj). Pour utiliser cette option, installez l’[extension Projets de Visual Studio Installer](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Vous pouvez aussi installer les composants prérequis pour les applications de poste de travail en configurant un programme d’installation générique, appelé programme d’amorçage. Pour plus d’informations, consultez [Prérequis du déploiement d’applications](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Déployer sur un laboratoire de test

Vous pouvez effectuer des développements et des tests plus sophistiqués en déployant vos applications dans des environnements virtuels. Pour plus d'informations, consultez [Tester sur un environnement lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Déploiement continu

Vous pouvez utiliser Azure Pipelines pour permettre le déploiement continu de votre application. Pour plus d’informations, consultez [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) et [Déployer sur Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Déploiement pour d’autres types d’application

| Type d'application | Scénario de déploiement | Lien |
| --- | --- | --- |
| **Application Office** | Vous pouvez publier un complément pour Office à partir de Visual Studio. | [Déployer et publier votre complément Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Service WCF ou OData** | D’autres applications peuvent utiliser des services RIA WCF que vous déployez sur un serveur web. | [Développement et déploiement de WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch n’est plus pris en charge à partir de Visual Studio 2017, mais peut encore être déployé à partir de Visual Studio 2015 et versions antérieures. | [Déploiement d’applications LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez eu un bref aperçu des options de déploiement pour différentes applications.

> [!div class="nextstepaction"]
> [Quelles options de publication choisir ?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
