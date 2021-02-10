---
title: Création de fonctionnalités SharePoint | Microsoft Docs
description: Créez une fonctionnalité SharePoint pour regrouper les éléments de projet SharePoint associés afin de faciliter le déploiement. Ajoutez des fonctionnalités à la solution SharePoint. Utilisez le concepteur de fonctionnalités.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc572f6fc5c0444fda619af5af49c6c2e52ac5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949114"
---
# <a name="create-sharepoint-features"></a>Créer des fonctionnalités SharePoint
  Vous pouvez utiliser une fonctionnalité SharePoint pour regrouper des éléments de projet SharePoint connexes pour faciliter le déploiement. Vous pouvez créer des fonctionnalités, définir des étendues et marquer d’autres fonctionnalités en tant que dépendances à l’aide du concepteur de fonctionnalités SharePoint. Le concepteur génère également un manifeste, qui est un fichier XML décrivant chaque fonctionnalité.

## <a name="add-features-to-the-sharepoint-solution"></a>Ajouter des fonctionnalités à la solution SharePoint
 Vous pouvez ajouter une fonctionnalité à la solution SharePoint à l’aide de Explorateur de solutions ou de l’Explorateur de package. Vous pouvez utiliser l’une des méthodes suivantes pour ajouter une fonctionnalité.

- Dans **Explorateur de solutions**, ouvrez le menu contextuel des **fonctionnalités**, puis choisissez **Ajouter une fonctionnalité**.

- Dans l' **Explorateur de packages**, ouvrez le menu contextuel du package, puis choisissez Ajouter une **fonctionnalité**.

## <a name="using-the-feature-designer"></a>Utilisation du concepteur de fonctionnalités
 Une solution SharePoint peut contenir une ou plusieurs fonctionnalités SharePoint, qui sont regroupées sous le nœud Feature dans Explorateur de solutions. Chaque fonctionnalité possède son propre **Concepteur de fonctionnalités** que vous pouvez utiliser pour personnaliser les propriétés de la fonctionnalité. Pour plus d’informations, consultez [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Pour distinguer les fonctionnalités les unes des autres, vous pouvez configurer les propriétés des fonctionnalités telles que le titre, la description, la version et l’étendue.

### <a name="feature-designer-options"></a>Options du concepteur de fonctionnalités
 Après avoir créé une fonctionnalité, vous pouvez utiliser le concepteur de fonctionnalités pour la personnaliser.

 Le tableau suivant décrit les propriétés de fonctionnalité qui s’affichent dans le concepteur de fonctionnalités.

|Propriété|Description|
|--------------|-----------------|
|Title|Facultatif. Le titre par défaut de la fonctionnalité a la valeur *SolutionName* *NomFonctionnalité*.|
|Description|facultatif. Description de la fonctionnalité SharePoint.|
|Étendue|Obligatoire. Si une fonctionnalité est créée à l’aide de **Explorateur de solutions**, l’étendue est définie sur Web par défaut.<br /><br /> -Batterie de serveurs : activer une fonctionnalité pour une batterie de serveurs entière.<br /><br /> -Site : active une fonctionnalité pour tous les sites Web d’une collection de sites.<br /><br /> -Web : active une fonctionnalité pour un site Web spécifique.<br /><br /> -WebApplication : active une fonctionnalité pour tous les sites Web d’une application Web.|
|Éléments de la solution|Tous les éléments SharePoint qui peuvent être ajoutés à la fonctionnalité.|
|Éléments dans la fonctionnalité|Éléments de projet SharePoint qui ont été ajoutés à la fonctionnalité.|

## <a name="add-and-remove-sharepoint-project-items"></a>Ajouter et supprimer des éléments de projet SharePoint
 Vous pouvez sélectionner les éléments de projet SharePoint auxquels vous souhaitez ajouter une fonctionnalité SharePoint pour le déploiement. Utilisez le **Concepteur de fonctionnalités** pour ajouter et supprimer des éléments dans les fonctionnalités, et pour afficher le manifeste de la fonctionnalité. Pour plus d’informations, consultez [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Ajouter des dépendances de fonctionnalités
 Vous pouvez configurer le manifeste de fonctionnalité de sorte que le serveur SharePoint active certaines fonctionnalités avant que votre fonctionnalité soit activée. Par exemple, si votre fonctionnalité SharePoint dépend d’autres fonctionnalités de fonctionnalités ou de données, le serveur SharePoint peut tout d’abord essayer d’activer l’une des fonctionnalités dont dépend votre fonctionnalité. Pour plus d’informations, consultez [Comment : ajouter et supprimer des dépendances de fonctionnalités](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Voir aussi
- [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Comment : ajouter et supprimer des dépendances de fonctionnalités](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
