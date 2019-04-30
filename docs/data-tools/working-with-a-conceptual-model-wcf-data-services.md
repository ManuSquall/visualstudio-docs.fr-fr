---
title: Utilisation d’un modèle conceptuel (services de données WCF)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: df9c1f83e8a839c7e767c3145e734eba80add485
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566075"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Travailler avec un modèle conceptuel (WCF Data Services)

Lorsque vous utilisez un modèle conceptuel pour décrire les données dans une base de données, vous pouvez interroger les données via vos objets au lieu de devoir traduire dans les deux sens entre un schéma de base de données et un modèle d’objet.

 Vous pouvez utiliser des modèles conceptuels avec les applications WCF Data Services. Les rubriques suivantes montrent comment interroger des données via un modèle conceptuel.

| Rubrique | Description |
| - | - |
| [Guide pratique pour Exécuter des requêtes de Service de données](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Montre comment interroger un service de données à partir d’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] application. |
| [Guide pratique pour Résultats de la requête](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Montre comment réduire la quantité de données retournées par une requête de service de données. |

 Lorsque vous utilisez un modèle conceptuel, vous pouvez définir le type de données est valide dans la langue qui correspond à votre domaine. Vous pouvez définir des données valides dans le modèle, ou vous pouvez ajouter la validation pour les opérations que vous effectuez sur un service de l’entité ou de données.

 Les rubriques suivantes montrent comment ajouter la validation pour les applications WCF Data Services.

|Rubrique|Description|
|-----------|-----------------|
|[Guide pratique pour Intercepter des messages de Service de données](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Montre comment ajouter une validation à une opération de service de données.|

 Les rubriques suivantes montrent comment créer, mettre à jour et supprimer des données en effectuant des opérations sur les entités.

|Rubrique|Description|
|-----------|-----------------|
|[Guide pratique pour Ajouter, modifier et supprimer des entités](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Montre comment créer, mettre à jour et supprimer des données d’entité dans un service de données.|
|[Guide pratique pour Définir des relations d’entité](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Montre comment créer ou modifier des relations dans un service de données.|

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Interrogation du service de données](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)