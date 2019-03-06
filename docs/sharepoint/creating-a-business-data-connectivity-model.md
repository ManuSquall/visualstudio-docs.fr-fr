---
title: Création d’un modèle de connectivité de données métiers | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4873085a4e4508b40b866eee79e79f624f3c01d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605729"
---
# <a name="create-a-business-data-connectivity-model"></a>Créer un modèle de connectivité de données métiers
  Vous pouvez créer un modèle de connectivité de données métiers (BDC) ou personnaliser un modèle BDC existant à l’aide de Visual Studio. Chaque projet SharePoint peut contenir qu’un seul modèle. Pour plus d’informations, consultez [intégrer des données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Créer un nouveau modèle
 Pour créer un nouveau modèle, créez un **modèle de connectivité de données métiers** de projet ou ajouter un **modèle de connectivité de données métiers** d’élément à un **projet SharePoint vide**.

> [!NOTE]
>  Vous devez avoir [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installé sur votre ordinateur.

 Visual Studio ajoute un dossier au projet. Ce dossier porte le nom que vous spécifiez pour le **modèle de connectivité de données métiers** d’élément dans le **ajouter un nouvel élément** boîte de dialogue. Si vous créez un nouveau **modèle de connectivité de données métiers** projet, Visual Studio nomme le dossier **BdcModel1**.

 Visual Studio ajoute les fichiers suivants vers le nouveau dossier :

|Fichier|Description|
|----------|-----------------|
|Fichier de définition de modèle|Contient du code XML qui définit les entités, des méthodes, des objets de système métier (LOB) et d’autres métadonnées qui décrit le modèle.<br /><br /> Modifier les métadonnées dans ce fichier en utilisant le concepteur BDC, **Explorateur BDC**, **détails de méthode BDC** fenêtre, et **propriétés** fenêtre.|
|Fichier de Code de Service Entity|Contient des méthodes qui récupèrent, mettre à jour et suppriment des instances de l’entité par défaut.|

 Pour définir les propriétés d’une entité, modifiez le fichier de code d’entité. Pour plus d'informations, voir [Procédure : Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Pour récupérer, mettre à jour et suppriment des instances d’une entité, ajoutez le code au fichier de code de service entité. Pour plus d’informations, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

 Lorsque vous compilez le projet, Visual Studio crée un assembly. Vérifiez que vous n’ajoutez pas d’autres éléments au projet qui ajoutent du code à l’assembly de projet (par exemple : un **Workflow séquentiel** élément ou un **WebPart** élément). Le code pour cet élément ne s’exécutera pas lorsque vous déployez la solution, car le package de solution ne copie pas de l’assembly dans le global assembly cache.  Le package de solution déploie l’assembly sur la base de données BDC dans SharePoint uniquement.

> [!NOTE]
>  Visual Studio copie l’assembly dans les deux emplacements sur votre ordinateur local lorsque vous déboguez le projet.

## <a name="add-an-existing-model"></a>Ajouter un modèle existant
 Vous pouvez importer un modèle qui a été créé à l’aide d’autres outils tels que SharePoint Designer. Vous pouvez choisir d’importer un modèle existant à votre projet dans les situations suivantes :

- Pour personnaliser un modèle qui est déjà déployé dans une batterie de serveurs SharePoint.

- Pour empaqueter et déployer un modèle existant sur plusieurs batteries de serveurs SharePoint.

  Dans les deux cas, les systèmes métier définies dans le modèle que vous importez ne sont pas affectées et continuent de fonctionner comme prévu. Pour ajouter un modèle existant à un projet SharePoint, utilisez Visual Studio **ajouter un élément existant** boîte de dialogue. Pour plus d'informations, voir [Procédure : Ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Vous pouvez ajouter un système métier de l’assembly de type .NET Framework au modèle importé en sélectionnant une option dans le **LobSystem d’assembly .NET ajouter**. Cela vous permet à écrire du code personnalisé et utiliser un concepteur pour définir les métadonnées du modèle importé.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Guide pratique pour Créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)|Vous montre comment créer un modèle BDC.|
|[Guide pratique pour Ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Vous montre comment importer un modèle existant dans un projet SharePoint.|
|[Guide pratique pour Utilisez un fichier de ressources pour spécifier des autorisations, les propriétés et les noms localisés](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Décrit comment fournir des chaînes qui sont fusionnées avec les métadonnées de modèle lorsque le modèle est consommé par un composant WebPart ou une Page Web.|
|[Guide pratique pour Inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Vous montre comment inclure un assembly personnalisé dans la fonctionnalité.|
