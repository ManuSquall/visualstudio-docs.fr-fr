---
title: Intégration de données métiers dans SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4bbfb681a0dac0825bf7af4f1f27ab1c1b50053
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016314"
---
# <a name="integrate-business-data-into-sharepoint"></a>Intégrer des données métiers dans SharePoint
  Vous pouvez intégrer des données métier dans SharePoint. Les données métier peuvent provenir d’applications serveur principales, telles que [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)] , Siebel et SAP, ou d’un service Web. Les utilisateurs peuvent afficher, ajouter, mettre à jour ou supprimer des données d’entreprise à l’aide de listes externes ou de composants WebPart de données d’entreprise dans SharePoint.  Les utilisateurs peuvent également accéder à ces données hors connexion dans une application Microsoft Office telle que Microsoft Outlook. Pour plus d’informations, consultez la page [où vous pouvez afficher des données externes](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Pour intégrer des données dans SharePoint, créez un modèle pour le service de connectivité de données métiers (BDC). Le service BDC est une application dans SharePoint qui stocke des informations sur les données des applications d’entreprise. Pour plus d’informations, consultez [service de connectivité de données métiers (BDC)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modèles dans Visual Studio
 Les modèles dans Visual Studio vous permettent d’écrire du code personnalisé pour récupérer et mettre à jour des données à partir de sources de données principales. Vous pouvez également agréger des données à partir de plusieurs sources de données. Par exemple, vous pouvez afficher une liste de clients qui contient des données d’une [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] base de données et d’un service Web.

 Vous pouvez également importer des modèles qui sont déjà déployés sur SharePoint. Après avoir importé un modèle, vous pouvez ajouter du code personnalisé ou simplement utiliser Visual Studio pour empaqueter et déployer le modèle sur plusieurs batteries de serveurs SharePoint. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Concevoir un modèle dans Visual Studio
 Vous pouvez concevoir un modèle à l’aide d’un concepteur et de plusieurs fenêtres outil. Au fur et à mesure que vous concevez le modèle, Visual Studio génère le modèle XML. Pour plus d’informations, consultez [vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Un modèle contient des entités et des méthodes.

### <a name="entities"></a>Entités
 Une entité décrit une collection de champs. Par exemple, une entité peut représenter une table dans une base de données. Une entité apparaît sous la forme d’un type de contenu externe dans SharePoint. Pour plus d’informations sur les types de contenu externes, consultez [qu’est-ce qu’un type de contenu externe ?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Méthodes
 Une méthode permet aux consommateurs d’un type de contenu externe d’exécuter une action sur les champs d’une entité. Par exemple, une méthode de mise à jour peut permettre aux utilisateurs de modifier l’adresse et la date de naissance d’un client où `Address` et `BirthDate` sont des champs de l' `Customer` entité.

 Visual Studio génère un fichier de code de service pour chaque entité de votre modèle. Quand vous ajoutez une méthode à votre modèle, Visual Studio génère une méthode correspondante dans le fichier de code de service. Ajoutez du code à chaque méthode pour effectuer la tâche appropriée. Par exemple, si vous ajoutez une méthode Creator au modèle, Visual Studio génère une méthode Creator dans votre fichier de code de service. Cette méthode est appelée par le service BDC lorsqu’un utilisateur clique sur le bouton **nouvel élément** dans une liste basée sur le modèle. Par conséquent, ajoutez du code à la méthode Creator qui ajoute de nouvelles données à une source de données. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)|Montre comment créer un modèle ou importer un modèle que vous exportez à partir de SharePoint.|
|[Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)|Explique comment concevoir les éléments d’un modèle à l’aide des outils de conception de Visual Studio.|
|[Quand utiliser SharePoint Designer ou Visual Studio lors de la création de solutions à l’aide de BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Vous aide à décider s’il convient d’utiliser Visual Studio ou d’utiliser SharePoint Designer pour créer un modèle pour le BDC.|
