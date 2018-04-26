---
title: Quelles options de publication choisir ?
ms.date: 03/09/2017
ms.reviewer: riande
ms.prod: visual-studio-dev15
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18c0a5c24f664d337df3d85f24078d7ed410c137
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# Quelles options de publication choisir ?

À partir de Visual Studio, les applications web peuvent être publiées directement dans les cibles suivantes :

- [Azure App Service](#azure-app-service)
- [Machines virtuelles Azure](#azure-virtual-machines)
- [Système de fichiers](#file-system)
- [Cibles personnalisées (IIS, FTP, etc.)](#custom-targets), y compris tous les serveurs web arbitraires.

Sous l’onglet **Publier**, vous pouvez sélectionner un profil de publication existant, en importer un ou en créer un à l’aide des options décrites ici. Vous trouverez une présentation des options de publication dans l’environnement de développement intégré (IDE) pour différents types d’applications sur la page [Premier aperçu du déploiement](../../deployment/deploying-applications-services-and-components.md).

## Azure App Service Web Apps

[Azure App Service Web Apps](/azure/app-service/app-service-web-overview) (ou simplement Web Apps) permet aux développeurs de créer rapidement différentes applications web et services évolutifs sans gestion d’infrastructure.

Vous déterminez la puissance de calcul d’une application web en choisissant un [plan ou niveau tarifaire](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pour l’App Service qui le contient. Vous pouvez avoir plusieurs applications web (et d’autres types d’application) qui partagent le même plan App Service sans modifier le niveau tarifaire. Par exemple, vous pouvez héberger des applications web de développement, intermédiaires et de production dans le même plan App Service.

Un plan App Service s’exécute sur des machines virtuelles hébergées dans le cloud Azure, mais ces machines virtuelles sont gérées pour vous. Chaque application Web d’un plan App Service reçoit une URL *.azurewebsites.net \* unique. Tous les niveaux tarifaires payants permettent d’attribuer des noms de domaine personnalisés au site.

### Quand choisir Azure App Service Web Apps ?

- Vous voulez déployer une application web accessible par Internet.
- Vous voulez automatiquement mettre à l’échelle votre application web en fonction de la demande sans avoir à la redéployer.
- Vous ne voulez pas gérer l’infrastructure de serveur (y compris les mises à jour logicielles).
- Vous n’avez pas besoin de personnaliser les ordinateurs serveur qui hébergent votre application web.

> Si vous voulez utiliser Azure App Service dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Pour plus d’informations sur la publication des applications ASP.NET Core, consultez [Publier une application web ASP.NET Core sur Azure App Service à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## Machines virtuelles Azure

Le service [Machines virtuelles Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) permet de créer et gérer des ressources informatiques dans le cloud. Si vous prenez en charge tous les logiciels et les mises à jour sur les machines virtuelles, vous pouvez les personnaliser comme vous le souhaitez en fonction des besoins de votre application web. Vous pouvez également accéder aux machines virtuelles directement via le Bureau à distance, chaque machine conservant son adresse IP aussi longtemps que vous le souhaitez.

La mise à l’échelle d’une application web hébergée sur des machines virtuelles implique l’ajout de machines virtuelles supplémentaires en fonction de la demande et le déploiement des logiciels nécessaires. Ce niveau de contrôle supplémentaire vous permet de moduler la mise à l’échelle selon la région globale. Par exemple, si votre application est utilisée par les employés de différents bureaux régionaux, vous pouvez mettre à l’échelle vos machines virtuelles en fonction du nombre d’employés dans ces régions et ainsi potentiellement réduire les coûts.

Pour plus d’informations, reportez-vous à la [comparaison détaillée](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) d’Azure App Service, Machines virtuelles Azure et d’autres services Azure que vous pouvez utiliser comme cible de déploiement à l’aide de l’option Personnalisé dans Visual Studio.

### Quand choisir le service Machines virtuelles Azure

- Vous voulez déployer une application web accessible par Internet, avec un contrôle total sur la durée de vie des adresses IP attribuées.
- Vous avez besoin de personnaliser vos ordinateurs serveur, notamment installer des logiciels supplémentaires, par exemple, un système de base de données spécialisé, des configurations réseau spécifiques, des partitions de disque et ainsi de suite.
- Vous voulez contrôler la mise à l’échelle de votre application web.
- Vous avez besoin d’un accès direct aux serveurs qui hébergent votre application.

> Si vous voulez utiliser le service Machines virtuelles Azure dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## Système de fichiers

Le déploiement sur le système de fichiers revient à copier les fichiers de votre application web dans un dossier spécifique sur votre ordinateur. Cela est souvent utilisé à des fins de test ou pour déployer l’application pour un nombre limité d’utilisateurs si l’ordinateur exécute également un serveur web. Si le dossier cible est partagé sur un réseau, le déploiement sur le système de fichiers permet de mettre les fichiers de l’application web à la disposition d’autres utilisateurs qui peuvent ensuite la déployer sur des serveurs spécifiques.

Les ordinateurs locaux qui exécutent un serveur web peuvent rendre votre application disponible sur Internet ou un intranet en fonction de sa configuration et des réseaux auxquels il est connecté. (Si vous connectez un ordinateur directement à Internet, protégez-le des menaces de sécurité externes.) Comme vous gérez ces ordinateurs, vous avez un contrôle total sur les configurations matérielles et logicielles.

Notez que, si pour une raison quelconque (par exemple, l’accès à l’ordinateur), vous n’êtes pas en mesure d’utiliser les services cloud comme Azure App Service ou Machines virtuelles Azure, vous pouvez utiliser [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) dans votre centre de données. Azure Stack vous permet de gérer et d’utiliser localement les ressources informatiques grâce à Azure App Service et les Machines virtuelles Azure.

### Quand choisir le déploiement sur un système de fichiers

- Vous avez besoin de déployer l’application uniquement sur un partage de fichiers à partir duquel d’autres utilisateurs la déploieront sur différents serveurs.
- Vous avez besoin d’un déploiement de test local uniquement.
- Vous voulez examiner et éventuellement modifier les fichiers d’application indépendamment avant de les envoyer vers une autre cible de déploiement.

Pour plus d’informations sur le déploiement des applications .NET Core, consultez [Déploiement des applications .NET Core avec Visual Studio](/dotnet/core/deploying/deploy-with-vs).

## Cibles personnalisées

Une cible personnalisée vous permet de déployer votre application web sur une autre cible qu’Azure App Service, les Machines virtuelles Azure ou le système de fichiers local. Elle peut effectuer le déploiement sur un système de fichiers ou tout autre serveur (Internet ou intranet) auquel vous avez accès, y compris sur d’autres services cloud. Elle peut fonctionner avec Web Deploy (fichiers ou. ZIP) et FTP.

Quand vous choisissez une cible personnalisée, Visual Studio vous demande un nom de profil, puis collecte des informations de **connexion** supplémentaires, y compris le serveur ou l’emplacement cible, un nom de site et des informations d’identification. Vous pouvez contrôler les comportements suivants sur l’onglet **Paramètres** :

- La configuration que vous souhaitez déployer.
- Si vous souhaitez supprimer des fichiers existants à partir de la destination.
- Si vous souhaitez précompiler durant la publication.
- Si vous souhaitez exclure des fichiers dans le dossier App_Data issu du déploiement.

Vous pouvez créer autant de profils de déploiement personnalisés dans Visual Studio que nécessaire, ce qui permet de gérer les profils avec des paramètres différents.

### Quand choisir le déploiement personnalisé

- Vous utilisez des services cloud sur un autre fournisseur qu’Azure accessible via des URL.
- Vous voulez effectuer le déploiement à l’aide d’autres informations d’identification que celles que vous utilisez dans Visual Studio ou que celles directement liées à vos comptes Azure.
- Vous voulez supprimer les fichiers de la cible à chaque déploiement.

Pour plus d’informations sur la publication sur IIS, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) et [Débogage distant de ASP.NET sur un ordinateur IIS distant](../../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).