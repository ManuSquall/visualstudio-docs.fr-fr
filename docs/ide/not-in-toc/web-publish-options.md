---
title: "Quelles options de publication choisir ? | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2017
ms.reviewer: riande
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: "1"
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 10cb0ca2d5190ce73f0fd67da5b1f795d5aa8dd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# Quelles options de publication choisir ?

À partir de Visual Studio, les applications web peuvent être publiées directement dans les cibles suivantes :

- [Azure App Service](#azure-app-service)
- [Machines virtuelles Azure](#azure-virtual-machines)
- [Système de fichiers](#file-system)
- [Cibles personnalisées (IIS, FTP, etc.)](#custom-targets), y compris tous les serveurs web arbitraires.

Sous l’onglet **Publier**, vous pouvez sélectionner un profil de publication existant, en importer un ou en créer un à l’aide des options décrites ici.

## Azure App Service

[Azure App Service](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/) permet aux développeurs de créer rapidement différentes applications web et services évolutifs sans gestion d’infrastructure.

Pour les applications web en particulier, un plan App Service est le conteneur d’une [*application web*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/), qui s’apparente à un hôte web classique. Autrement dit, une application web fournit les ressources de calcul nécessaires pour exécuter votre code côté serveur et le rendre disponible sur Internet.

Vous déterminez la puissance de calcul d’une application web en choisissant un [plan ou niveau tarifaire](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/) pour l’App Service qui le contient. Vous pouvez avoir plusieurs applications web (et d’autres types d’application) qui partagent le même plan App Service sans modifier le niveau tarifaire. Par exemple, vous pouvez héberger des applications web de développement, intermédiaires et de production dans le même plan App Service.

Un plan App Service s’exécute sur des machines virtuelles hébergées dans le cloud Azure, mais ces machines virtuelles sont gérées pour vous. Chaque application Web d’un plan App Service reçoit une URL *.azurewebsites.net \* unique. Tous les niveaux tarifaires payants permettent d’attribuer des noms de domaine personnalisés au site.

### Quand choisir Azure App Service

- Vous voulez déployer une application web accessible par Internet.
- Vous voulez automatiquement mettre à l’échelle votre application web en fonction de la demande sans avoir à la redéployer.
- Vous ne voulez pas gérer l’infrastructure de serveur (y compris les mises à jour logicielles).
- Vous n’avez pas besoin de personnaliser les ordinateurs serveur qui hébergent votre application web.


> Si vous voulez utiliser Azure App Service dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


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
