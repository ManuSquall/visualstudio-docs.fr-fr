---
title: Configurer un projet de service cloud Azure avec Visual Studio | Microsoft Docs
description: Découvrez comment configurer un projet de service cloud Azure dans Visual Studio, selon vos spécifications pour ce projet.
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 7417bc117de7dc472f413dd9145944cad2d48bb4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002013"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Configurer un projet de service cloud Azure avec Visual Studio
Vous pouvez configurer un projet de service cloud Azure, selon vos spécifications pour ce projet. Vous pouvez définir les propriétés du projet pour les catégories suivantes :

- **Publier un service cloud sur Azure** -vous pouvez définir une propriété pour vous assurer qu’un service cloud existant déployé sur Azure n’est pas effacé accidentellement.
- **Exécuter ou déboguer un service cloud sur l’ordinateur local** -vous pouvez sélectionner une configuration de service à utiliser et indiquer si vous souhaitez démarrer l’émulateur de stockage Azure.
- **Valider un package de service de cloud lors de sa création** -vous pouvez décider de traiter tous les avertissements comme des erreurs afin que vous pouvez vous assurer que le package de service cloud se déploie sans problèmes. 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Étapes pour configurer un projet de service cloud Azure
1. Ouvrez ou créez un projet de service cloud dans Visual Studio

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis, dans le menu contextuel, sélectionnez **propriétés**.
   
1. Dans la page de propriétés du projet, sélectionnez le **développement** onglet.

    ![Menu des propriétés du projet](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Définissez **demander confirmation avant la suppression d’un déploiement existant** à **True**. Ce paramètre permet de garantir que vous ne supprimez pas accidentellement un déploiement existant dans Azure

1. Sélectionnez l’élément **configuration du Service** pour indiquer la configuration de service que vous souhaitez utiliser lorsque vous exécutez ou déboguez localement votre service cloud. Pour plus d’informations sur la façon de modifier une configuration de service pour un rôle, consultez [comment configurer les rôles pour un service cloud Azure avec Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Définissez **émulateur de stockage Azure Démarrer** à **True** pour démarrer l’émulateur de stockage Azure lorsque vous exécutez ou déboguez localement votre service cloud.

1. Définissez **considérer les avertissements comme des erreurs** à **True** s’assurer que vous ne pouvez pas publier s’il existe des erreurs de validation de package.

1. Définissez **utiliser les ports du projet web** à **True** pour vous assurer que votre rôle web utilise le même port chaque fois qu’elle démarre localement dans IIS Express.

1. Dans la barre d’outils Visual Studio, sélectionnez **enregistrer**.

## <a name="next-steps"></a>Étapes suivantes
- [Configurer un projet Windows Azure à l’aide de plusieurs configurations de service](vs-azure-tools-multiple-services-project-configurations.md)

