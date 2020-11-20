---
title: Utilisation d’un modèle conceptuel (services de données WCF)
description: Utilisez un modèle conceptuel dans WCF Data Services. Interroger des données à l’aide d’objets au lieu de les traduire entre les schémas de base de données et les modèles d’objet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2aa79ca10729b9c36437fe30072328838de5dda4
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94997873"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Utiliser un modèle conceptuel (WCF Data Services)

Lorsque vous utilisez un modèle conceptuel pour décrire les données d’une base de données, vous pouvez interroger les données via vos objets au lieu de passer d’un schéma de base de données à un modèle d’objet.

Vous pouvez utiliser des modèles conceptuels avec des applications WCF Data Services. Les rubriques suivantes montrent comment interroger des données via un modèle conceptuel.

| Rubrique | Description |
| - | - |
| [Comment : exécuter des requêtes de service de données](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Montre comment interroger un service de données à partir d’une application .NET. |
| [Comment : projeter des résultats de requête](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Montre comment réduire la quantité de données retournées par le biais d’une requête de service de données. |

Lorsque vous utilisez un modèle conceptuel, vous pouvez définir le type de données valide dans la langue qui correspond à votre domaine. Vous pouvez définir des données valides dans le modèle, ou vous pouvez ajouter la validation aux opérations que vous effectuez sur une entité ou un service de données.

Les rubriques suivantes montrent comment ajouter la validation aux applications WCF Data Services.

|Rubrique|Description|
|-----------|-----------------|
|[Comment : intercepter des messages de service de données](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Montre comment ajouter une validation à une opération de service de données.|

 Les rubriques suivantes montrent comment créer, mettre à jour et supprimer des données en effectuant des opérations sur des entités.

|Rubrique|Description|
|-----------|-----------------|
|[Procédure : ajouter, modifier et supprimer des entités](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Montre comment créer, mettre à jour et supprimer des données d’entité dans un service de données.|
|[Comment : définir des relations d’entité](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Montre comment créer ou modifier des relations dans un service de données.|

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Interrogation du service de données](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
