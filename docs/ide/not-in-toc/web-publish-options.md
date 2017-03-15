---
title: "Quelles options de publication choisir ? | Microsoft Docs"
ms.custom: 
ms.date: 1/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 85a7f3ef705d3b110ab0dc39d08d0cee235bf307
ms.openlocfilehash: 1ecb87d748a7770101bdf6e0ffe34250a36c97a8
ms.lasthandoff: 02/22/2017

---

# <a name="what-publishing-options-are-right-for-me"></a>Quelles options de publication choisir ?

À partir de Visual Studio, les applications web peuvent être publiées directement dans les cibles suivantes :

- [Azure App Service](#azure-app-service)
- [Machines virtuelles Azure](#azure-virtual-machines)
- [Système de fichiers](#file-system)
- [Cibles personnalisées (IIS, FTP, etc.)](#custom-targets), y compris tous les serveurs web arbitraires.

Sous l’onglet **Publier**, vous pouvez sélectionner un profil de publication existant, en importer un ou en créer un à l’aide des options décrites ici. 

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](https://azure.microsoft.com/documentation/articles/app-service-value-prop-what-is/) permet aux développeurs de créer rapidement différentes applications web et services évolutifs sans gestion d’infrastructure.

Pour les applications web en particulier, un plan App Service est le conteneur d’une [*application web*](https://azure.microsoft.com/en-us/documentation/articles/app-service-web-overview/), qui s’apparente à un hôte web classique. Autrement dit, une application web fournit les ressources de calcul nécessaires pour exécuter votre code côté serveur et le rendre disponible sur Internet.

Vous déterminez la puissance de calcul d’une application web en choisissant un [plan ou niveau tarifaire](https://azure.microsoft.com/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/)) pour l’App Service qui le contient. Vous pouvez également avoir plusieurs applications web (et d’autres types d’application) qui partagent le même plan App Service sans modifier le niveau tarifaire. Par exemple, vous pouvez héberger des applications web de développement, intermédiaires et de production dans le même plan App Service. 

Un plan App Service s’exécute sur des machines virtuelles hébergées dans le cloud Azure, mais ces machines virtuelles sont gérées pour vous. Chaque application web d’un plan App Service reçoit une URL *.azurewebsites.net unique. Tous les niveaux tarifaires payants permettent également d’attribuer des noms de domaine personnalisés au site.  

### <a name="when-to-choose-azure-app-service"></a>Quand choisir Azure App Service

- Vous voulez déployer une application web accessible par Internet.
- Vous voulez automatiquement mettre à l’échelle votre application web en fonction de la demande sans avoir à la redéployer.
- Vous ne voulez pas gérer l’infrastructure de serveur (y compris toutes les mises à jour logicielles).
- Vous n’avez pas besoin de personnaliser les ordinateurs serveur qui hébergent votre application web.


> Si vous voulez utiliser Azure App Service dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## <a name="azure-virtual-machines"></a>Machines virtuelles Azure

Le service [Machines virtuelles Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) permet de créer et gérer des ressources informatiques dans le cloud. Si vous prenez en charge tous les logiciels et les mises à jour sur les machines virtuelles, vous pouvez les personnaliser comme vous le souhaitez en fonction des besoins de votre application web. Vous pouvez également accéder aux serveurs directement via le Bureau à distance, chaque serveur conservant son adresse IP aussi longtemps que vous le souhaitez.

La mise à l’échelle d’une application web hébergée sur des machines virtuelles implique l’ajout de machines virtuelles supplémentaires en fonction de la demande et le déploiement des logiciels nécessaires. Ce niveau de contrôle supplémentaire vous permet de moduler la mise à l’échelle selon la région globale. Par exemple, si votre application est utilisée par les employés de différents bureaux régionaux, vous pouvez mettre à l’échelle vos machines virtuelles en fonction du nombre d’employés dans ces régions et ainsi potentiellement réduire les coûts. 

Pour plus d’informations, reportez-vous à la [comparaison détaillée](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) d’Azure App Service, Machines virtuelles Azure et d’autres services Azure que vous pouvez utiliser comme cible de déploiement à l’aide de l’option Personnalisé dans Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Quand choisir le service Machines virtuelles Azure

- Vous voulez déployer une application web accessible par Internet, avec un contrôle total sur la durée de vie des adresses IP attribuées.
- Vous avez besoin de personnaliser vos ordinateurs serveur, notamment installer des logiciels supplémentaires, par exemple, un système de base de données spécialisé, des configurations réseau spécifiques, des partitions de disque et ainsi de suite.
- Vous voulez contrôler la mise à l’échelle de votre application web.
- Vous avez besoin d’un accès direct aux serveurs qui hébergent votre application.

> Si vous voulez utiliser le service Machines virtuelles Azure dans votre centre de données ou sur d’autres ordinateurs locaux, vous pouvez le faire à l’aide d’[Azure Stack](https://azure.microsoft.com/overview/azure-stack/).


## <a name="file-system"></a>Système de fichiers

Le déploiement sur le système de fichiers revient à copier les fichiers de votre application web dans un dossier spécifique sur votre ordinateur. Cela est souvent utilisé à des fins de test ou pour déployer l’application pour un nombre limité d’utilisateurs si l’ordinateur exécute également un serveur web. Si le dossier cible est partagé sur un réseau, le déploiement sur le système de fichiers permet également de mettre les fichiers de l’application web à la disposition d’autres utilisateurs qui peuvent ensuite la déployer sur des serveurs spécifiques.  

Les ordinateurs locaux qui exécutent un serveur web peuvent rendre votre application disponible sur Internet ou un intranet en fonction de sa configuration et des réseaux auxquels il est connecté. (Si vous connectez un ordinateur directement à Internet, protégez-le des menaces de sécurité externes.) Comme vous gérez ces ordinateurs, vous avez un contrôle total sur les configurations matérielles et logicielles. 

Notez que, si pour une raison quelconque (par exemple, l’accès à l’ordinateur), vous n’êtes pas en mesure d’utiliser les services cloud comme Azure App Service ou Machines virtuelles Azure, vous pouvez utiliser [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) dans votre centre de données. Azure Stack vous permet de gérer et d’utiliser localement les ressources informatiques grâce à Azure App Service et les Machines virtuelles Azure.  

### <a name="when-to-choose-file-system-deployment"></a>Quand choisir le déploiement sur un système de fichiers

- Vous avez besoin de déployer l’application uniquement sur un partage de fichiers à partir duquel d’autres utilisateurs la déploieront sur différents serveurs.
- Vous avez besoin d’un déploiement de test local uniquement.
- Vous voulez examiner et éventuellement modifier les fichiers d’application indépendamment avant de les envoyer vers une autre cible de déploiement.



## <a name="custom-targets"></a>Cibles personnalisées

Une cible personnalisée vous permet de déployer votre application web sur une autre cible qu’Azure App Service, les Machines virtuelles Azure ou le système de fichiers local. Elle peut effectuer le déploiement sur un système de fichiers ou tout autre serveur (Internet ou intranet) auquel vous avez accès, y compris sur d’autres services cloud. Elle peut fonctionner avec Web Deploy (fichiers ou. ZIP) et FTP. 

Quand vous choisissez une cible personnalisée, Visual Studio vous demande un nom de profil, puis collecte des informations de **connexion** supplémentaires, y compris le serveur ou l’emplacement cible, un nom de site et des informations d’identification. Vous pouvez également contrôler certains comportements de l’onglet **Paramètres** comme la configuration à déployer, s’il faut supprimer les fichiers existants dans la destination, s’il faut précompiler pendant la publication et s’il faut ignorer les fichiers du dossier App_Data du déploiement. 

Vous pouvez créer autant de profils de déploiement personnalisés dans Visual Studio que nécessaire, ce qui permet de gérer les profils avec des paramètres légèrement différents en fonction des besoins.

### <a name="when-to-choose-custom-deployment"></a>Quand choisir le déploiement personnalisé

- Vous utilisez des services cloud sur un autre fournisseur qu’Azure accessible via des URL.
- Vous voulez effectuer le déploiement à l’aide d’autres informations d’identification que celles que vous utilisez dans Visual Studio ou que celles directement liées à vos comptes Azure.
- Vous voulez supprimer les fichiers de la cible à chaque déploiement. 


