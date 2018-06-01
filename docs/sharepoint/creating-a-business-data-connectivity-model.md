---
title: Création d’un modèle de connectivité de données métiers | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c6fc0b1169ff906d7cda36eeeb5a74410cf46a9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691494"
---
# <a name="creating-a-business-data-connectivity-model"></a>Création d’un modèle de connectivité de données métiers
  Vous pouvez créer un modèle de connectivité de données métiers (BDC) ou personnaliser un modèle BDC existant à l’aide de Visual Studio. Chaque projet SharePoint peut contenir qu’un seul modèle. Pour plus d’informations, consultez [intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Créer un nouveau modèle
 Pour créer un nouveau modèle, créez un **modèle de connectivité de données métiers** ou ajoutez un **modèle de connectivité de données métiers** d’élément à un **projet SharePoint vide**.  
  
> [!NOTE]  
>  Vous devez avoir [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installé sur votre ordinateur.  
  
 Visual Studio ajoute un dossier au projet. Ce dossier porte le nom que vous spécifiez pour le **modèle de connectivité de données métiers** d’élément dans le **ajouter un nouvel élément** boîte de dialogue. Si vous créez un nouveau **modèle de connectivité de données métiers** projet, Visual Studio nomme le dossier **BdcModel1**.  
  
 Visual Studio ajoute les fichiers suivants vers le nouveau dossier :  
  
|Fichier|Description|  
|----------|-----------------|  
|Fichier de définition de modèle|Contient du code XML qui définit les entités, les méthodes, les objets du système métier (LOB) et les autres métadonnées qui décrivent le modèle.<br /><br /> Modifier les métadonnées dans ce fichier à l’aide du concepteur BDC, **Explorateur BDC**, **détails de méthode BDC** fenêtre, et **propriétés** fenêtre.|  
|Fichier de Code de Service entité|Contient des méthodes pour récupèrent, mettre à jour et suppriment des instances de l’entité par défaut.|  
  
 Pour définir les propriétés d’une entité, modifiez le fichier de code d’entité. Pour plus d’informations, consultez [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Pour récupérer, mettre à jour et supprimer des instances d’une entité, ajoutez le code au fichier de code entité service. Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Lorsque vous compilez le projet, Visual Studio crée un assembly. Assurez-vous que vous n’ajoutez pas d’autres éléments au projet qui ajoutent du code à l’assembly de projet (par exemple : un **Workflow séquentiel** élément ou un **WebPart** élément). Le code de cet élément ne fonctionnera pas lorsque vous déployez la solution, car le package de solution ne copie pas de l’assembly dans le global assembly cache.  Le package de solution déploie l’assembly dans la base de données catalogue de données métiers dans SharePoint uniquement.  
  
> [!NOTE]  
>  Visual Studio copie l’assembly dans les deux emplacements sur votre ordinateur local lorsque vous déboguez le projet.  
  
## <a name="add-an-existing-model"></a>Ajouter un modèle existant
 Vous pouvez importer un modèle qui a été créé à l’aide d’autres outils tels que SharePoint Designer. Vous pouvez choisir d’importer un modèle existant à votre projet dans les situations suivantes :  
  
-   Pour personnaliser un modèle qui est déjà déployé sur une batterie de serveurs SharePoint.  
  
-   Pour empaqueter et déployer un modèle existant sur plusieurs batteries de serveurs SharePoint.  
  
 Dans les deux cas, les systèmes métier définies dans le modèle que vous importez ne sont pas affectées et continuent à fonctionner comme prévu. Pour ajouter un modèle existant à un projet SharePoint, utilisez Visual Studio **ajouter un élément existant** boîte de dialogue. Pour plus d’informations, consultez [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 Vous pouvez ajouter un système LOB de l’assembly de type .NET Framework au modèle importé en sélectionnant une option dans le **ajouter un assembly .NET LobSystem**. Cela vous permet à écrire du code personnalisé et utiliser un concepteur pour définir les métadonnées du modèle importé.  
  
## <a name="related-topics"></a>Rubriques connexes
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)|Vous montre comment créer un modèle BDC.|  
|[Guide pratique pour ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Montre comment importer un modèle existant dans un projet SharePoint.|  
|[Guide pratique pour utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Décrit comment fournir des chaînes qui sont fusionnées avec les métadonnées de modèle lorsque le modèle est consommé par un composant ou une Page Web.|  
|[Guide pratique pour inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Vous montre comment inclure un assembly personnalisé dans la fonction.|  
  
 