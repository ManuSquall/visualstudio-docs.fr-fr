---
title: Présentation des fonctionnalités de déploiement
description: En savoir plus sur les options disponibles pour le déploiement d’applications à partir de Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9198e39be5149440b09ebab5115e803d60716423
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080261"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Démarrage rapide : Premier aperçu au moment du déploiement dans Visual Studio

En déployant une application, un service ou un composant, vous le distribuez pour l’installation sur d’autres ordinateurs, appareils ou serveurs, ou dans le cloud. Vous choisissez la méthode appropriée dans Visual Studio pour le type de déploiement dont vous avez besoin. (Nombreux types d’application prend en charge les autres outils de déploiement telles que le déploiement de la ligne de commande ou NuGet qui ne sont pas décrites ici).

Consultez les Démarrages rapides et didacticiels pour obtenir des instructions de déploiement étape par étape. Pour une vue d’ensemble des options de déploiement, consultez [quelles options de publication sont me convient ?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Déployer sur le dossier local

Déploiement vers un dossier local est généralement utilisé pour le test ou pour lancer un déploiement intermédiaire dans lequel un autre outil est utilisé pour le déploiement final.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, et. **NET Core**: utiliser l’outil de publication pour déployer vers un dossier local. Les options disponibles dépendent de votre type d’application. Dans l’Explorateur de solutions, cliquez sur votre projet et choisissez **publier**. (Si vous avez déjà configuré des profils de publication, vous devez ensuite cliquer sur **créer nouveau profil**.) Ensuite, choisissez **dossier**. Pour plus d’informations, consultez [déployer vers un dossier local](quickstart-deploy-to-local-folder.md).

    ![Choisissez publier](../deployment/media/quickstart-publish.png)

- **Visual C++ runtime**: vous pouvez déployer le runtime Visual C++ à l’aide de déploiement local ou liaison statique. Pour plus d’informations, consultez [déploiement d’Applications de bureau natives (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

## <a name="publish-to-azure"></a>Publier sur Azure

- **ASP.NET**, **ASP.NET Core**, **Python**, et **Node.js**: vous pouvez utiliser l’outil de publication pour déployer rapidement des applications sur Azure App Service ou à un commutateur Azure Machine. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**. (Si vous avez déjà configuré des profils de publication, vous devez ensuite cliquer sur **créer nouveau profil**.) Dans la boîte de dialogue Publier, choisissez **App Service** ou **Machines virtuelles**, puis suivez les étapes de configuration.

    ![Choisissez Azure App Service](../deployment/media/quickstart-publish-azure.png "choisir Azure App Service")

    Dans Visual Studio 2017 version 15.7 et ultérieure, vous pouvez déployer des applications ASP.NET Core **App Service pour Linux**.

    Pour les applications Python, consultez également [Python - publication sur Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Pour plus d’informations sur l’importation d’un profil de publication à partir d’Azure App Service pour Visual Studio, consultez [importer les paramètres de publication et la déployer dans Azure](../deployment/tutorial-import-publish-settings-azure.md).

    Pour une présentation rapide, consultez [publier sur Azure](quickstart-deploy-to-azure.md). En outre, consultez [publier une application ASP.NET Core sur Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Pour le déploiement à l’aide de Git, consultez [déploiement continu d’ASP.NET Core sur Azure avec Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Si vous n’avez pas déjà un compte Azure, vous pouvez [Inscrivez-vous ici](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publier sur le Web ou le déployer sur un partage réseau

- **ASP.NET**, **ASP.NET Core**, **Node.js**, et **Python**: vous pouvez utiliser l’outil de publication pour déployer sur un site Web à l’aide de FTP ou Web Deploy. Pour plus d’informations, consultez [déployer vers un site web](quickstart-deploy-to-a-web-site.md).

    Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**. (Si vous avez déjà configuré des profils de publication, vous devez ensuite cliquer sur **créer nouveau profil**.) Dans l’outil de publication, choisissez l’option souhaitée et suivez les étapes de configuration.

    ![Choisissez IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Pour plus d’informations sur l’importation d’un profil de publication dans Visual Studio, consultez [importer les paramètres de publication et la déployer sur IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Vous pouvez également déployer des applications ASP.NET et services dans plusieurs autres façons. Pour plus d’informations, consultez [ASP.NET de déploiement d’applications et services web](http://www.asp.net/aspnet/overview/deployment).

- **Visual C++ runtime**: vous pouvez déployer le runtime Visual C++ à l’aide de déploiement central. Pour plus d’informations, consultez [déploiement d’Applications de bureau natives (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Bureau de Windows** vous pouvez publier une application de bureau Windows à un serveur web ou un partage de fichiers réseau à l’aide du déploiement ClickOnce. Les utilisateurs peuvent ensuite installer l'application d'un seul clic. Pour plus d’informations, consultez [déployer une application de bureau à l’aide de ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) et [déployer une application native à l’aide de ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Publier sur Microsoft Store

À partir de Visual Studio, vous pouvez créer des packages d’application pour le déploiement sur Microsoft Store.

- **UWP**: vous pouvez empaqueter votre application et le déployer à l’aide des éléments de menu. Pour plus d’informations, consultez [empaqueter une application UWP à l’aide de Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Création d'un package d'application](../deployment/media/feature-tour-create-app-package.jpg)

- **Bureau de Windows**: vous pouvez déployer sur le Microsoft Store à l’aide de Desktop Bridge à partir de Visual Studio 2017 version 15.4. Pour ce faire, commencez par créer un projet de package d’Application Windows. Pour plus d’informations, consultez [empaqueter une application de bureau pour Microsoft Store (pont du bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Pont de bureau](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Déployer sur un appareil (UWP)

Si vous déployez une application UWP pour le test sur un appareil, consultez [exécuter des applications UWP sur un ordinateur distant dans Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Créer un package d’installation (client Windows)

Si vous avez besoin plus d’une installation complexe d’une application de bureau que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) peut fournir, vous pouvez créer un package d’installation, un projet d’installation ou un programme d’amorçage personnalisé.

- Un programme d’installation WiX basé sur MSI peut être créé à l’aide de la [Extension WiX Toolset Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) à partir de Flexera Software peut être utilisée avec Visual Studio 2017 (Community Edition ne pas pris en charge). Notez que InstallShield Limited Edition n’est plus incluse avec Visual Studio et n’est pas pris en charge dans Visual Studio 2017 ; Vérifiez auprès de [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sur la disponibilité des futures.

- Si vous souhaitez créer un projet d’installation (vdproj), installez le [extension des projets de programme d’installation de Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Vous pouvez installer les composants requis pour les applications bureautiques en configurant un programme d’installation générique, qui est connu comme un programme d’amorçage. Pour plus d’informations, consultez [conditions préalables au déploiement de Application](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Déployer pour le laboratoire de test

Vous pouvez activer plus sophistiquées de développement et de test en déployant vos applications dans des environnements virtuels. Pour plus d’informations, consultez [Test sur un environnement lab](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Déploiement de DevOps

Dans un environnement d’équipe, vous pouvez utiliser Visual Studio Team Services (VSTS) pour activer le déploiement continu de votre application. Pour plus d’informations, consultez [Build et de publication](/vsts/build-release/index) et [déployer sur Azure](/vsts/deploy-azure/index).

## <a name="deployment-for-other-app-types"></a>Déploiement pour les autres types d’application

| Type d'application | Scénario de déploiement | Lien |
| --- | --- | --- |
| **Application Office** | Vous pouvez publier un complément pour Office à partir de Visual Studio. | [Déployer et publier votre complément Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Service WCF ou OData**  | Autres applications peuvent utiliser les services RIA WCF que vous déployez sur un serveur web. | [Développement et le déploiement des Services de données WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch n’est plus pris en charge dans Visual Studio 2017, mais pourra être déployé à partir de Visual Studio 2015 et versions antérieures. | [Déploiement d’Applications LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez examiné rapide des options de déploiement pour différentes applications.

> [!div class="nextstepaction"]
> [Quelles options de publication sont me convient ?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
