---
title: "Vue d’ensemble du déploiement - Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e05bf361515b45f3ebc7683fa0c83ec6116d9419
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="deployment-overview-in-visual-studio"></a>Vue d’ensemble du déploiement dans Visual Studio

En déployant une application, un service ou un composant, vous le distribuez pour l'installation sur d'autres ordinateurs, périphériques, serveurs ou dans le cloud. Vous choisissez la méthode appropriée dans Visual Studio pour le type de déploiement dont vous avez besoin. (Plusieurs types d’application prennent en charge les autres outils de déploiement telles que le déploiement de la ligne de commande ou de NuGet qui ne sont pas décrits ici).

Consultez les didacticiels pour obtenir des instructions pas à pas.

### <a name="deploy-to-local-folder"></a>Déployer vers un dossier local

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, et **.NET Core**: utiliser l’outil de publication pour déployer dans une variable locale dossier. Les options disponibles dépendent de votre type d’application. Dans l’Explorateur de solutions, avec le bouton droit de votre projet et choisissez **publier**, puis choisissez **dossier**. Pour plus d’informations, consultez [déployer vers un dossier local](quickstart-deploy-to-local-folder.md).

    ![Choisissez publier](../deployment/media/quickstart-publish.png)

- **Visual C++ runtime**: vous pouvez déployer le runtime Visual C++ à l’aide d’un déploiement local ou la liaison statique. Pour plus d’informations, consultez [déploiement d’Applications de bureau natives (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Publier sur le Web ou le déployer sur un partage réseau

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, et **.NET Core**: vous pouvez utiliser l’outil de publication pour déployer sur un site Web à l’aide de FTP ou Web Deploy. Pour plus d’informations, consultez [déployer vers un site web](quickstart-deploy-to-a-web-site.md).

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**. Dans l’outil de publication, choisissez l’option souhaitée, suivez les étapes de configuration.

    ![Choisissez IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Vous pouvez également déployer des applications ASP.NET et services dans un nombre d’autres façons. Pour plus d’informations, consultez [ASP.NET de déploiement d’applications et services web](http://www.asp.net/aspnet/overview/deployment).

- **Visual C++ runtime**: vous pouvez déployer le runtime Visual C++ à l’aide de déploiement central. Pour plus d’informations, consultez [déploiement d’Applications de bureau natives (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Bureau Windows** vous pouvez publier une application de bureau Windows à un serveur web ou un partage de fichiers réseau à l’aide du déploiement ClickOnce. Les utilisateurs peuvent ensuite installer l'application d'un seul clic. Pour plus d’informations, consultez [déployer une application de bureau à l’aide de ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) et [déployer une application native à l’aide de ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Publier sur Azure

- **ASP.NET, ASP.NET Core, Python, Node.js et .NET Core** des applications web : vous pouvez utiliser l’outil de publication pour déployer rapidement des applications vers Azure App Service ou à une Machine virtuelle de Azure. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**. Dans la boîte de dialogue Publier, choisissez **Microsoft Azure App Service** ou **des Machines virtuelles Microsoft Azure**, puis suivez les étapes de configuration.

    ![Choisissez le Service d’applications Azure](../deployment/media/quickstart-publish-azure.png "choisissez Azure App Service")

    Pour publier vers une Machine virtuelle de Azure, défilement vers la droite et sélectionnez **des Machines virtuelles Microsoft Azure**.

    Pour une présentation rapide, consultez [publier sur Azure](quickstart-deploy-to-azure.md). Consultez également [publier une application ASP.NET Core dans Windows Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Pour le déploiement à l’aide de Git, consultez [déploiement continu de ASP.NET Core dans Azure avec Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Si vous n’avez pas déjà un compte Azure, vous pouvez [Inscrivez-vous ici](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

- Autres **services Azure**: consultez spécifique au [service Azure](/azure/#pivot=products) documentation pour les différentes options de déploiement qui peut être pris en charge par Visual Studio.

### <a name="publish-to-microsoft-store"></a>Publier sur Microsoft Store

À partir de Visual Studio, vous pouvez créer des packages d’application pour un déploiement vers Microsoft Store.

- **UWP**: vous pouvez empaqueter votre application et le déployer à l’aide des éléments de menu. Pour plus d’informations, consultez [empaqueter une application UWP à l’aide de Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Création d'un package d'application](../deployment/media/feature-tour-create-app-package.jpg)

- **Bureau Windows**: vous pouvez déployer sur Microsoft Store à l’aide de la passerelle Bureau à partir de Visual Studio 2017 version 15.4. Pour ce faire, commencez par créer un projet de package d’Application Windows. Pour plus d’informations, consultez [empaqueter une application de bureau pour Microsoft Store (pont bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Pont de bureau](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Créer un package d’installation (client Windows)

- Un programme d’installation basé sur le fichier MSI de WiX peut être créé à l’aide de la [WiX ensemble d’outils Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera logiciel peut être utilisé avec Visual Studio 2017 (Community Edition ne pas pris en charge). Notez que InstallShield Limited Edition n’est plus inclus dans Visual Studio et n’est pas pris en charge dans Visual Studio 2017 ; Vérifiez auprès de [Flexera logiciel](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sur la disponibilité à venir.

- Si vous souhaitez créer un projet d’installation (vdproj), installez le [extension des projets de programme d’installation de Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Vous pouvez installer les composants requis pour les applications bureautiques en configurant un programme d’installation générique qui est connu comme un programme d’amorçage. Pour plus d’informations, consultez [conditions préalables au déploiement de Application](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Déployer pour le laboratoire de tests

Vous pouvez activer plus sophistiquées de développement et de test en déployant vos applications dans des environnements virtuels. Pour plus d’informations, consultez [Test sur un environnement lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>Déploiement de DevOps

Dans un environnement d’équipe, vous pouvez utiliser Visual Studio Team Services (VSTS) pour permettre un déploiement continu de votre application. Pour plus d’informations, consultez [créer et libérer](/vsts/build-release/index) et [déployer vers Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Déploiement pour les autres types d’application

| Type d'application | Scénario de déploiement | Lien |
| --- | --- | --- |
| **Applications Office** | Vous pouvez publier un complément pour Office à partir de Visual Studio. | [Déployer et publier votre complément Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Service WCF ou OData**  | Autres applications peuvent utiliser des services RIA WCF que vous déployez sur un serveur web. | [Développement et le déploiement des Services de données WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch n’est plus pris en charge dans Visual Studio 2017, mais peut toujours être déployée à partir de Visual Studio 2015 et versions antérieures. | [Déploiement d’Applications LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

