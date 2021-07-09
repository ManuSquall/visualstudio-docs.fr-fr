---
title: déployer votre application Visual Studio dans un dossier, IIS, Azure ou une autre destination
titleSuffix: ''
description: En savoir plus sur les options de publication pour votre application à l’aide de l’outil de publication.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
f1_keywords:
- vs.publish
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 099bd2c6cc47895c913b3f852835d2fd09d0f9c3
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549483"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Déployer votre application dans un dossier, IIS, Azure ou une autre destination

En déployant une application, un service ou un composant, vous le distribuez pour l'installation sur d'autres ordinateurs, périphériques, serveurs ou dans le cloud. Vous choisissez la méthode appropriée dans Visual Studio pour le type de déploiement dont vous avez besoin.

Obtenir de l’aide pour votre tâche de déploiement :

- Vous n’êtes pas sûr de l’option de déploiement à choisir ? [Quelles sont les options de publication qui me conviennent ?](#what-publishing-options-are-right-for-me)
- pour obtenir de l’aide sur les problèmes de déploiement de Azure App Service ou iis, consultez [résoudre les problèmes de ASP.NET Core sur Azure App Service et iis](/aspnet/core/test/troubleshoot-azure-iis).
- Pour obtenir de l’aide sur la configuration des paramètres de déploiement .NET, consultez [configurer les paramètres de déploiement .net](#configure-net-deployment-settings).
- Pour effectuer un déploiement vers une nouvelle cible, si vous avez déjà créé un profil de publication, sélectionnez **nouveau** dans la fenêtre **publier** pour un profil configuré.

   ![Créer un profil de publication](../deployment/media/create-a-new-publish-profile.png)

   Ensuite, choisissez une option de déploiement dans la fenêtre publier. Pour plus d’informations sur vos options de publication, consultez les sections suivantes.

## <a name="what-publishing-options-are-right-for-me"></a>Quelles options de publication choisir ?

À partir de Visual Studio, les applications peuvent être publiées directement sur les cibles suivantes :

::: moniker range=">=vs-2019"
- [Microsoft Azure](#azure)
- [Container Registry d’ancrage](#docker-container-registry)
- [Folder](#folder)
- [Serveur FTP/FTPS](#ftpftps-server)
- [Serveur Web (IIS)](#web-server-iis)
- [Importer le profil](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service Linux](#azure-app-service)
- [IIS (choisissez IIS, FTP, etc.)](#web-server-iis)
- [FTP/FTPS (choisissez IIS, FTP, etc.)](#ftpftps-server)
- [Folder](#folder)
- [Importer le profil](#import-profile)
::: moniker-end

Les options précédentes apparaissent comme indiqué dans l’illustration suivante lorsque vous créez un profil de publication.

::: moniker range=">=vs-2019"
![Choisir une option de publication](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Choisir une option de publication](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Pour une présentation rapide des options de déploiement d’applications plus générales, consultez [premier aperçu du déploiement](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Lorsque vous choisissez Azure, vous pouvez choisir entre les éléments suivants :

- [Azure App Service](#azure-app-service) s’exécutant sur Windows, Linux ou en tant qu’image de l’arrimeur
- Une image d’ancrage déployée sur [Azure Container Registry](#azure-container-registry)
- Une [machine virtuelle Azure](#azure-virtual-machine)

![Choisir un service Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App service](/azure/app-service/app-service-web-overview) aide les développeurs à créer rapidement des applications et des services Web évolutifs sans gérer l’infrastructure. Un plan App Service s’exécute sur des machines virtuelles hébergées dans le cloud Azure, mais ces machines virtuelles sont gérées pour vous. Chaque application d’un plan App Service reçoit une URL \*.azurewebsites.net unique. Tous les niveaux tarifaires payants permettent d’attribuer des noms de domaine personnalisés au site.

Vous déterminez la puissance de calcul d’un service d’applications en choisissant un [plan ou niveau tarifaire](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pour le plan App Service qui le contient. Vous pouvez avoir plusieurs applications web (et d’autres types d’application) qui partagent le même plan App Service sans modifier le niveau tarifaire. Par exemple, vous pouvez héberger des applications web de développement, de préproduction et de production dans le même plan App Service.

#### <a name="when-to-choose-azure-app-service"></a>Quand choisir Azure App Service

- Vous voulez déployer une application web accessible par Internet.
- Vous voulez automatiquement mettre à l’échelle votre application web en fonction de la demande sans avoir à la redéployer.
- Vous ne voulez pas gérer l’infrastructure de serveur (y compris les mises à jour logicielles).
- Vous n’avez pas besoin de personnaliser les ordinateurs serveur qui hébergent votre application web.

> Si vous voulez utiliser Azure App Service dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Pour plus d’informations sur la publication sur App Service, consultez :
- [Démarrage rapide-publier sur Azure App Service](quickstart-deploy-to-azure.md)
- [démarrage rapide : publiez des ASP.NET Core sur Linux](quickstart-deploy-to-linux.md).
- [publier une application ASP.NET Core sur Azure App Service](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [résolvez les problèmes de ASP.NET Core sur Azure App Service et IIS](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) vous permet de créer, de stocker et de gérer des images de conteneur et des artefacts d’ancrage dans un registre privé pour tous les types de déploiement de conteneur.

#### <a name="when-to-choose-azure-container-registry"></a>Quand choisir Azure Container Registry

- Lorsque vous disposez d’un pipeline de développement et de déploiement de conteneur d’ancrage.
- Lorsque vous souhaitez créer des images de conteneur d’ancrage dans Azure.

Pour plus d'informations :

- [déployer un conteneur ASP.NET dans un registre de conteneurs](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Machine virtuelle Azure

Les [machines virtuelles Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) vous permettent de créer et de gérer un nombre quelconque de ressources informatiques dans le Cloud. Si vous prenez en charge tous les logiciels et mises à jour sur les machines virtuelles, vous pouvez les personnaliser comme vous le souhaitez en fonction des besoins de votre application. Vous pouvez également accéder aux machines virtuelles directement via le Bureau à distance, chaque machine conservant son adresse IP aussi longtemps que vous le souhaitez.

La mise à l’échelle d’une application hébergée sur des machines virtuelles implique l’ajout de machines virtuelles supplémentaires en fonction de la demande et le déploiement des logiciels nécessaires. Ce niveau de contrôle supplémentaire vous permet de moduler la mise à l’échelle selon la région globale. Par exemple, si votre application est utilisée par les employés de différents bureaux régionaux, vous pouvez mettre à l’échelle vos machines virtuelles en fonction du nombre d’employés dans ces régions et ainsi potentiellement réduire les coûts.

Pour plus d’informations, consultez la [comparaison détaillée](/azure/architecture/guide/technology-choices/compute-decision-tree) entre les Azure App service, les machines virtuelles Azure et d’autres services Azure que vous pouvez utiliser comme cible de déploiement à l’aide de l’option personnalisée dans Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Quand choisir des machines virtuelles Azure

- Vous voulez déployer une application web accessible par Internet, avec un contrôle total sur la durée de vie des adresses IP attribuées.
- Vous avez besoin de personnalisations au niveau de l’ordinateur sur vos serveurs, notamment des logiciels supplémentaires tels qu’un système de base de données spécialisé, des configurations réseau spécifiques, des partitions de disque et ainsi de suite.
- Vous voulez contrôler la mise à l’échelle de votre application web.
- Vous avez besoin d’un accès direct aux serveurs qui hébergent votre application.

> Si vous voulez utiliser le service Machines virtuelles Azure dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Registre de conteneurs Docker

Si votre application utilise la station d’accueil, vous pouvez publier votre application en conteneur dans un registre de conteneurs de l’ancrage.

### <a name="when-to-choose-docker-container-registry"></a>Quand choisir l’Ancreur Container Registry

- Vous souhaitez déployer une application en conteneur

Pour plus d’informations, consultez les rubriques suivantes :

- [déployer un conteneur ASP.NET dans un registre de conteneurs](../containers/hosting-web-apps-in-docker.md)
- [Déployer sur Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Dossier

Le déploiement sur le système de fichiers consiste à copier les fichiers de votre application dans un dossier spécifique sur votre ordinateur. Le déploiement dans un dossier est le plus souvent utilisé à des fins de test, ou pour déployer l’application en vue d’une utilisation par un nombre limité de personnes si l’ordinateur exécute également un serveur. Si le dossier cible est partagé sur un réseau, le déploiement sur le système de fichiers permet de mettre les fichiers de l’application web à la disposition d’autres utilisateurs qui peuvent ensuite la déployer sur des serveurs spécifiques.
::: moniker range=">=vs-2019"
à compter de Visual Studio 2019 16,8, la cible de dossier offre la possibilité de publier une application .net Windows à l’aide de ClickOnce.

si vous souhaitez publier un .net Core 3,1, ou une version plus récente, Windows application avec ClickOnce, consultez [déployer une application .net Windows à l’aide de ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Les ordinateurs locaux qui exécutent un serveur peuvent rendre votre application disponible sur Internet ou un intranet en fonction de sa configuration et des réseaux auxquels il est connecté. (Si vous connectez un ordinateur directement à Internet, veillez particulièrement à le protéger contre les menaces de sécurité externes.) Étant donné que vous gérez ces machines, vous contrôlez entièrement les configurations logicielles et matérielles.

Si, pour une raison quelconque (par exemple, l’accès à la machine), vous n’êtes pas en mesure d’utiliser des services de Cloud Computing comme Azure App Service ou des machines virtuelles Azure, vous pouvez utiliser les [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) dans votre propre centre de donnée. Azure Stack vous permet de gérer et d’utiliser localement les ressources informatiques grâce à Azure App Service et les Machines virtuelles Azure.

### <a name="when-to-choose-file-system-deployment"></a>Quand choisir le déploiement sur un système de fichiers

- Vous avez besoin de déployer l’application uniquement sur un partage de fichiers à partir duquel d’autres utilisateurs la déploieront sur différents serveurs.
::: moniker range=">=vs-2019"
- vous souhaitez déployer une Application .net Windows à l’aide de ClickOnce
::: moniker-end
- Vous avez besoin d’un déploiement de test local uniquement.
- Vous voulez examiner et éventuellement modifier les fichiers d’application indépendamment avant de les envoyer vers une autre cible de déploiement.

Pour plus d’informations, consultez [démarrage rapide-déployer dans un dossier local](quickstart-deploy-to-local-folder.md).
::: moniker range=">=vs-2019"
pour plus d’informations sur le déploiement d’une application .net Windows à l’aide de ClickOnce, consultez [déployer une application .net Windows à l’aide de ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Pour obtenir une aide supplémentaire pour choisir vos paramètres, consultez les rubriques suivantes :

- [Déploiement dépendant du Framework et déploiement autonome](/dotnet/core/deploying/)
- [Identificateurs du runtime cible (RID portable, et al)](/dotnet/core/rid-catalog)
- [Configurations Debug et Release](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Serveur FTP/FTPS

Un serveur FTP/FTPS vous permet de déployer votre application sur un serveur autre que Azure. Elle peut effectuer le déploiement sur un système de fichiers ou tout autre serveur (Internet ou intranet) auquel vous avez accès, y compris sur d’autres services cloud. Elle peut fonctionner avec Web Deploy (fichiers ou. ZIP) et FTP.

lors du choix d’un serveur FTP/FTPS, Visual Studio vous invite à entrer un nom de profil, puis recueille des informations de **connexion** supplémentaires, y compris le serveur ou l’emplacement cible, un nom de site et des informations d’identification. Vous pouvez contrôler les comportements suivants sur l’onglet **Paramètres** :

- La configuration que vous souhaitez déployer.
- Si vous souhaitez supprimer des fichiers existants à partir de la destination.
- Si vous souhaitez précompiler durant la publication.
- Si vous souhaitez exclure des fichiers dans le dossier App_Data issu du déploiement.

vous pouvez créer un nombre quelconque de profils de déploiement FTP/FTPS dans Visual Studio, ce qui permet de gérer les profils avec des paramètres différents.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Quand choisir le déploiement du serveur FTP/FTPS

- Vous utilisez des services cloud sur un autre fournisseur qu’Azure accessible via des URL.
- Vous voulez effectuer le déploiement à l’aide d’autres informations d’identification que celles que vous utilisez dans Visual Studio ou que celles directement liées à vos comptes Azure.
- Vous voulez supprimer les fichiers de la cible à chaque déploiement.

## <a name="web-server-iis"></a>Serveur Web (IIS)

Un serveur Web IIS vous permet de déployer votre application sur un serveur Web autre qu’Azure. Il peut être déployé sur un serveur IIS (Internet ou intranet) auquel vous avez accès, y compris sur d’autres services Cloud. Il peut fonctionner avec Web Deploy ou un package Web Deploy.

lors du choix d’un serveur web IIS, Visual Studio vous invite à entrer un nom de profil, puis recueille des informations de **connexion** supplémentaires, y compris le serveur cible ou l’emplacement, un nom de site et des informations d’identification. Vous pouvez contrôler les comportements suivants sur l’onglet **Paramètres** :

- La configuration que vous souhaitez déployer.
- Si vous souhaitez supprimer des fichiers existants à partir de la destination.
- Si vous souhaitez précompiler durant la publication.
- Si vous souhaitez exclure des fichiers dans le dossier App_Data issu du déploiement.

vous pouvez créer autant de profils de déploiement de serveur web IIS que vous le souhaitez dans Visual Studio, ce qui permet de gérer les profils avec des paramètres différents.

### <a name="when-to-choose-web-server-iis-deployment"></a>Quand choisir le déploiement de serveur Web (IIS)

- Vous utilisez IIS pour publier un site ou un service accessible par le biais d’URL.
- Vous voulez effectuer le déploiement à l’aide d’autres informations d’identification que celles que vous utilisez dans Visual Studio ou que celles directement liées à vos comptes Azure.
- Vous voulez supprimer les fichiers de la cible à chaque déploiement.

Pour plus d’informations, consultez [démarrage rapide-déployer sur un site Web](quickstart-deploy-to-a-web-site.md).

pour obtenir de l’aide sur la résolution des ASP.NET Core sur iis, consultez [résoudre les problèmes ASP.NET Core sur Azure App Service et iis](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Profil d’importation

Vous pouvez importer un profil lors de la publication sur IIS ou Azure App Service. Vous pouvez configurer le déploiement à l’aide d’un *fichier de paramètres de publication* (*\* . publishsettings*). Un fichier de paramètres de publication est créé par IIS ou Azure App Service, il peut aussi être créé manuellement, pour ensuite être importé dans Visual Studio.

L’utilisation d’un fichier de paramètres de publication peut simplifier la configuration du déploiement et mieux fonctionner dans un environnement d’équipe, plutôt que de configurer manuellement chaque profil de déploiement.

### <a name="when-to-choose-import-profile"></a>Quand choisir le profil d’importation

- Vous publiez sur IIS et souhaitez simplifier la configuration du déploiement.
- Vous publiez sur IIS ou Azure App Service et souhaitez accélérer la configuration du déploiement en vue de sa réutilisation ou de la publication des membres de l’équipe sur le même service.

Pour plus d’informations, consultez les rubriques suivantes :

- [Importer des paramètres de publication et déployer sur IIS](tutorial-import-publish-settings-iis.md)
- [Importer des paramètres de publication et déployer sur Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Configurer les paramètres de déploiement .NET

Pour obtenir une aide supplémentaire pour choisir vos paramètres, consultez les rubriques suivantes :

- [Déploiement dépendant du Framework et déploiement autonome](/dotnet/core/deploying/)
- [Identificateurs du runtime cible (RID portable, et al)](/dotnet/core/rid-catalog)
- [Configurations Debug et Release](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Étapes suivantes

Tutoriels :

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [publier une application ASP.NET core dans Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Déploiement dans Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Déployer des applications UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publier une application Node.js sur Azure à l’aide de Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publier une application Python sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
