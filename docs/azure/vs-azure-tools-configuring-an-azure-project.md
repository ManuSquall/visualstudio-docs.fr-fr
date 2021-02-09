---
title: Configurer un projet de service cloud Azure
description: Découvrez comment configurer un projet de service cloud Azure dans Visual Studio selon vos spécifications pour ce projet.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: ad011e740d7bffeddf7f92bd3735fbeedc1f4020
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844253"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Configurer un projet de service cloud Azure avec Visual Studio
Vous pouvez configurer un projet de service cloud Azure selon vos spécifications pour ce projet. Vous pouvez définir des propriétés pour le projet pour les catégories suivantes :

- **Publier un service cloud sur Azure** - Vous pouvez définir une propriété pour vous assurer qu’un service cloud existant déployé sur Azure ne puisse pas être effacé accidentellement.
- **Exécuter ou déboguer un service Cloud sur l’ordinateur local** : vous pouvez sélectionner une configuration de service à utiliser et indiquer si vous voulez démarrer l’émulateur de stockage Azure.
- **Valider un package de service cloud lors de sa création** - Vous pouvez décider de traiter tous les avertissements comme des erreurs, afin de vous assurer que le package de service cloud se déploie sans problèmes.

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Étapes de configuration d’un projet de service cloud Azure
1. Ouvrir ou créer un projet de service cloud dans Visual Studio

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis, dans le menu contextuel, sélectionnez **Propriétés**.

1. Dans la page de propriétés du projet, sélectionnez l’onglet **Développement**.

    ![Menu des propriétés du projet](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Définissez **Demandez confirmation de la suppression d’un déploiement existant** sur **Vrai**. Ce paramètre permet de garantir que vous ne supprimez pas accidentellement un déploiement existant dans Azure

1. Sélectionnez une **configuration de service** pour indiquer la configuration de service que vous souhaitez utiliser lorsque vous exécutez ou déboguez localement votre service cloud. Pour plus d’informations sur la façon de modifier une configuration de service pour un rôle, consultez [Comment configurer les rôles pour un service cloud Azure avec Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Définissez **Démarrer l’émulateur de stockage Azure** sur **true** pour démarrer l’émulateur de stockage Azure lorsque vous exécutez ou déboguez votre service Cloud localement.

1. Définissez **Considérer les avertissements comme des erreurs** sur **Vrai** pour vous assurer que vous ne pouvez pas publier s’il y a des erreurs de validation du package.

1. Définissez **Utiliser les ports du projet web** sur **Vrai** pour vous assurer que votre rôle web utilise le même port à chaque démarrage local dans IIS Express.

1. Dans la barre d’outils de Visual Studio, sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes
- [Configurer un projet Azure à l'aide de plusieurs configurations de service](vs-azure-tools-multiple-services-project-configurations.md)
