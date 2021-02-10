---
title: Création d’un modèle de connectivité de données métiers | Microsoft Docs
description: Créer un modèle de connectivité de données métiers (BDC) ou personnaliser un modèle BDC existant à l’aide de Visual Studio. Chaque projet SharePoint ne peut contenir qu’un seul modèle.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8232847ce336ca559134aa1211a70057a1306faa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949257"
---
# <a name="create-a-business-data-connectivity-model"></a>Créer un modèle de connectivité de données métiers
  Vous pouvez créer un modèle de connectivité de données métiers (BDC) ou personnaliser un modèle BDC existant à l’aide de Visual Studio. Chaque projet SharePoint ne peut contenir qu’un seul modèle. Pour plus d’informations, consultez [intégrer des données métier dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Créer un modèle
 Pour créer un modèle, créez un projet de **modèle de connectivité de données métiers** ou ajoutez un élément de **modèle de connectivité de données métiers** à un **projet SharePoint vide**.

> [!NOTE]
> Vous devez avoir [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installé sur votre ordinateur.

 Visual Studio ajoute un dossier au projet. Ce dossier porte le nom que vous spécifiez pour l’élément de **modèle de connectivité de données métiers** dans la boîte de dialogue **Ajouter un nouvel élément** . Si vous créez un projet de **modèle de connectivité de données métiers** , Visual Studio nomme le dossier **BdcModel1**.

 Visual Studio ajoute les fichiers suivants au nouveau dossier :

|Fichier|Description|
|----------|-----------------|
|Fichier de définition de modèle|Contient des données XML qui définissent les entités, les méthodes, les objets système métier (LOB) et d’autres métadonnées qui décrivent le modèle.<br /><br /> Modifiez les métadonnées de ce fichier à l’aide du concepteur BDC, de l' **Explorateur BDC**, de la fenêtre Détails de la **méthode BDC** et de la fenêtre **Propriétés** .|
|Fichier de code du service d’entité|Contient des méthodes qui récupèrent, mettent à jour et suppriment des instances de l’entité par défaut.|

 Pour définir les propriétés d’une entité, modifiez le fichier de code de l’entité. Pour plus d’informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Pour récupérer, mettre à jour et supprimer des instances d’une entité, ajoutez du code au fichier de code du service d’entité. Pour plus d’informations, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

 Quand vous compilez le projet, Visual Studio crée un assembly. Veillez à ne pas ajouter d’autres éléments au projet qui ajoutent du code à l’assembly de projet (par exemple : un élément de **Workflow séquentiel** ou un élément **WebPart** ). Le code de cet élément ne s’exécute pas quand vous déployez la solution, car le package de solution ne copie pas l’assembly dans le Global Assembly Cache.  Le package de solution déploie l’assembly dans la base de données BDC dans SharePoint uniquement.

> [!NOTE]
> Visual Studio copie l’assembly dans les deux emplacements sur votre ordinateur local lorsque vous déboguez le projet.

## <a name="add-an-existing-model"></a>Ajouter un modèle existant
 Vous pouvez importer un modèle qui a été créé à l’aide d’autres outils, tels que SharePoint Designer. Vous pouvez choisir d’importer un modèle existant dans votre projet dans les cas suivants :

- Pour personnaliser un modèle qui est déjà déployé sur une batterie de serveurs SharePoint.

- Pour empaqueter et déployer un modèle existant dans plusieurs batteries de serveurs SharePoint.

  Dans les deux cas, les systèmes LOB définis dans le modèle que vous importez ne sont pas affectés et continuent de fonctionner comme prévu. Pour ajouter un modèle existant à un projet SharePoint, utilisez la boîte de dialogue **Ajouter un élément existant** de Visual Studio. Pour plus d’informations, consultez [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Vous pouvez ajouter un système LOB de type .NET Framework assembly au modèle importé en sélectionnant une option dans le **LobSystem ajouter un assembly .net**. Cela vous permet d’écrire du code personnalisé et d’utiliser un concepteur pour définir les métadonnées du modèle importé.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)|Montre comment créer un modèle BDC.|
|[Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Montre comment importer un modèle existant dans un projet SharePoint.|
|[Comment : utiliser un fichier de ressources pour spécifier des noms localisés, des propriétés et des autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Décrit comment fournir des chaînes fusionnées avec les métadonnées de modèle lorsque le modèle est consommé par un composant WebPart ou une page Web.|
|[Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Montre comment inclure un assembly personnalisé dans la fonctionnalité.|
