---
title: Vue d’ensemble du déploiement | Microsoft Docs
ms.custom: seodec18
ms.date: 06/22/2018
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdf11d31244ffca5c6a12e0661d34a8727301be0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952598"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Vue d’ensemble du déploiement dans Visual Studio

En déployant une application, un service ou un composant, vous le distribuez pour l'installation sur d'autres ordinateurs, périphériques, serveurs ou dans le cloud. Vous choisissez la méthode appropriée dans Visual Studio pour le type de déploiement dont vous avez besoin.

Pour de nombreux types d’application courants, vous pouvez déployer votre application directement à partir de l’Explorateur de solutions dans Visual Studio. Pour une présentation rapide de cette fonctionnalité, consultez [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md).

![Choisir une option de publication](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Quelles options de publication choisir ?

À partir de Visual Studio, les applications peuvent être publiées directement sur les cibles suivantes :

- [Azure App Service](#azure-app-service)
- [Machines virtuelles Azure](#azure-virtual-machines)
- [Système de fichiers](#file-system)
- [Cibles personnalisées (IIS, FTP, etc.)](#custom-targets), y compris tous les serveurs web arbitraires.

Sous l’onglet **Publier**, vous pouvez sélectionner un profil de publication existant, en importer un ou en créer un à l’aide des options décrites ici. Vous trouverez une présentation des options de publication dans l’environnement de développement intégré (IDE) pour différents types d’applications sur la page [Premier aperçu du déploiement](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) et [App Service sur Linux](/azure/app-service/containers/app-service-linux-intro) permettent aux développeurs de créer rapidement différentes applications et services web scalables sans gestion d’infrastructure.

Vous déterminez la puissance de calcul d’un service d’applications en choisissant un [plan ou niveau tarifaire](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pour le plan App Service qui le contient. Vous pouvez avoir plusieurs applications web (et d’autres types d’application) qui partagent le même plan App Service sans modifier le niveau tarifaire. Par exemple, vous pouvez héberger des applications web de développement, de préproduction et de production dans le même plan App Service.

Un plan App Service s’exécute sur des machines virtuelles hébergées dans le cloud Azure, mais ces machines virtuelles sont gérées pour vous. Chaque application d’un plan App Service reçoit une URL \*.azurewebsites.net unique. Tous les niveaux tarifaires payants permettent d’attribuer des noms de domaine personnalisés au site.

### <a name="when-to-choose-azure-app-service"></a>Quand choisir Azure App Service

- Vous voulez déployer une application web accessible par Internet.
- Vous voulez automatiquement mettre à l’échelle votre application web en fonction de la demande sans avoir à la redéployer.
- Vous ne voulez pas gérer l’infrastructure de serveur (y compris les mises à jour logicielles).
- Vous n’avez pas besoin de personnaliser les ordinateurs serveur qui hébergent votre application web.

> Si vous voulez utiliser Azure App Service dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Pour plus d’informations sur la publication sur App Service, consultez [Démarrage rapide - Publier sur Azure App Service](quickstart-deploy-to-azure.md) et [Démarrage rapide - Publier ASP.NET Core sur Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Machines virtuelles Azure

Le service [Machines virtuelles Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) permet de créer et gérer des ressources informatiques dans le cloud. Si vous prenez en charge tous les logiciels et mises à jour sur les machines virtuelles, vous pouvez les personnaliser comme vous le souhaitez en fonction des besoins de votre application. Vous pouvez également accéder aux machines virtuelles directement via le Bureau à distance, chaque machine conservant son adresse IP aussi longtemps que vous le souhaitez.

La mise à l’échelle d’une application hébergée sur des machines virtuelles implique l’ajout de machines virtuelles supplémentaires en fonction de la demande et le déploiement des logiciels nécessaires. Ce niveau de contrôle supplémentaire vous permet de moduler la mise à l’échelle selon la région globale. Par exemple, si votre application est utilisée par les employés de différents bureaux régionaux, vous pouvez mettre à l’échelle vos machines virtuelles en fonction du nombre d’employés dans ces régions et ainsi potentiellement réduire les coûts.

Pour plus d’informations, reportez-vous à la [comparaison détaillée](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) d’Azure App Service, Machines virtuelles Azure et d’autres services Azure que vous pouvez utiliser comme cible de déploiement à l’aide de l’option Personnalisé dans Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Quand choisir le service Machines virtuelles Azure

- Vous voulez déployer une application web accessible par Internet, avec un contrôle total sur la durée de vie des adresses IP attribuées.
- Vous avez besoin de personnaliser vos ordinateurs serveur, notamment installer des logiciels supplémentaires, par exemple, un système de base de données spécialisé, des configurations réseau spécifiques, des partitions de disque et ainsi de suite.
- Vous voulez contrôler la mise à l’échelle de votre application web.
- Vous avez besoin d’un accès direct aux serveurs qui hébergent votre application.

> Si vous voulez utiliser le service Machines virtuelles Azure dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>Système de fichiers

Le déploiement sur le système de fichiers revient à copier les fichiers de votre application dans un dossier spécifique sur votre ordinateur. Ce type de déploiement est souvent utilisé à des fins de test ou pour déployer l’application pour un nombre limité d’utilisateurs si l’ordinateur exécute également un serveur. Si le dossier cible est partagé sur un réseau, le déploiement sur le système de fichiers permet de mettre les fichiers de l’application web à la disposition d’autres utilisateurs qui peuvent ensuite la déployer sur des serveurs spécifiques.

Les ordinateurs locaux qui exécutent un serveur peuvent rendre votre application disponible sur Internet ou un intranet en fonction de sa configuration et des réseaux auxquels il est connecté. (Si vous connectez un ordinateur directement à Internet, protégez-le des menaces de sécurité externes.) Comme vous gérez ces ordinateurs, vous avez un contrôle total sur les configurations matérielles et logicielles.

Notez que, si pour une raison quelconque (par exemple, l’accès à l’ordinateur), vous n’êtes pas en mesure d’utiliser les services cloud comme Azure App Service ou Machines virtuelles Azure, vous pouvez utiliser [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) dans votre centre de données. Azure Stack vous permet de gérer et d’utiliser localement les ressources informatiques grâce à Azure App Service et les Machines virtuelles Azure.

### <a name="when-to-choose-file-system-deployment"></a>Quand choisir le déploiement sur un système de fichiers

- Vous avez besoin de déployer l’application uniquement sur un partage de fichiers à partir duquel d’autres utilisateurs la déploieront sur différents serveurs.
- Vous avez besoin d’un déploiement de test local uniquement.
- Vous voulez examiner et éventuellement modifier les fichiers d’application indépendamment avant de les envoyer vers une autre cible de déploiement.

Pour plus d’informations, consultez [Démarrage rapide - Déployer dans un dossier local](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Cibles personnalisées (IIS, FTP)

Une cible personnalisée vous permet de déployer votre application sur une autre cible qu’Azure App Service, les Machines virtuelles Azure ou le système de fichiers local. Elle peut effectuer le déploiement sur un système de fichiers ou tout autre serveur (Internet ou intranet) auquel vous avez accès, y compris sur d’autres services cloud. Elle peut fonctionner avec Web Deploy (fichiers ou. ZIP) et FTP.

Quand vous choisissez une cible personnalisée, Visual Studio vous demande un nom de profil, puis collecte des informations de **connexion** supplémentaires, y compris le serveur ou l’emplacement cible, un nom de site et des informations d’identification. Vous pouvez contrôler les comportements suivants sur l’onglet **Paramètres** :

- La configuration que vous souhaitez déployer.
- Si vous souhaitez supprimer des fichiers existants à partir de la destination.
- Si vous souhaitez précompiler durant la publication.
- Si vous souhaitez exclure des fichiers dans le dossier App_Data issu du déploiement.

Vous pouvez créer autant de profils de déploiement personnalisés dans Visual Studio que nécessaire, ce qui permet de gérer les profils avec des paramètres différents.

### <a name="when-to-choose-custom-deployment"></a>Quand choisir le déploiement personnalisé

- Vous utilisez des services cloud sur un autre fournisseur qu’Azure accessible via des URL.
- Vous voulez effectuer le déploiement à l’aide d’autres informations d’identification que celles que vous utilisez dans Visual Studio ou que celles directement liées à vos comptes Azure.
- Vous voulez supprimer les fichiers de la cible à chaque déploiement.

Pour plus d’informations, consultez [Démarrage rapide - Déployer sur un site web](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Étapes suivantes

Tutoriels :

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publier une application ASP.NET Core sur Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Déploiement dans Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Déployer des applications UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publier une application Node.js sur Azure à l’aide de Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publier une application Python sur Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
