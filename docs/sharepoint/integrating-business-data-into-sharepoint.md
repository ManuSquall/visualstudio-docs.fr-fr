---
title: Intégration de données métiers dans SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 194f2e0c88a0cbce9ef34f77246cf7969066833e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934438"
---
# <a name="integrate-business-data-into-sharepoint"></a>Intégrer des données métiers dans SharePoint
  Vous pouvez intégrer des données métiers dans SharePoint. Données d’entreprise peuvent provenir d’applications de serveur principal, tel que [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel et SAP, ou un service Web. Les utilisateurs peuvent afficher, ajouter, mettre à jour ou supprimer des données d’entreprise à l’aide des listes externes ou WebPart Business Data dans SharePoint.  Ils peuvent également accéder ces données hors connexion dans une application Microsoft Office telles que Microsoft Outlook. Pour plus d’informations, consultez [où peut vous afficher les données externes](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Pour intégrer des données dans SharePoint, créez un modèle pour le service de connectivité de données métiers (BDC). Le service BDC est une application dans SharePoint qui stocke des informations sur les données dans les applications métier. Pour plus d’informations, consultez [Service de connectivité de données métiers (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modèles dans Visual Studio  
 Modèles dans Visual Studio permettent d’écrire du code personnalisé pour récupérer et mettre à jour des données à partir de sources de données back-end. Vous pouvez également agréger des données à partir de plusieurs sources de données. Par exemple, vous pouvez afficher une liste de clients qui contient les données à partir d’un [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] de base de données et un service Web.  
  
 Vous pouvez également importer des modèles qui sont déjà déployés sur SharePoint. Après avoir importé un modèle, vous pouvez ajouter du code personnalisé ou simplement utiliser Visual Studio pour empaqueter et déployer le modèle sur plusieurs batteries de serveurs SharePoint. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="design-a-model-in-visual-studio"></a>Concevoir un modèle dans Visual Studio
 Vous pouvez concevoir un modèle à l’aide d’un concepteur et plusieurs fenêtres d’outils. Lorsque vous concevez le modèle, Visual Studio génère le modèle XML. Pour plus d’informations, consultez [vue d’ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Un modèle contient des entités et des méthodes.  
  
### <a name="entities"></a>Entités  
 Une entité décrit une collection de champs. Par exemple, une entité peut représenter une table dans une base de données. Une entité apparaît comme un type de contenu externe dans SharePoint. Pour plus d’informations sur les types de contenu externe, consultez [quels sont les Types de contenu externe ?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Méthodes  
 Une méthode offre aux utilisateurs d’un type de contenu externe à exécuter une action sur les champs d’une entité. Par exemple, une méthode de mise à jour peut permettre aux utilisateurs de modifier l’adresse et date de naissance d’un client où `Address` et `BirthDate` sont des champs de la `Customer` entité.  
  
 Visual Studio génère un fichier de code de service pour chaque entité dans votre modèle. Lorsque vous ajoutez une méthode à votre modèle, Visual Studio génère une méthode correspondante dans le fichier de code de service. Ajoutez le code à chaque méthode pour effectuer la tâche appropriée. Par exemple, si vous ajoutez une méthode de création pour le modèle, Visual Studio génère une méthode de création dans votre fichier de code de service. Cette méthode est appelée par le service BDC lorsqu’un utilisateur clique sur le **un nouvel élément** bouton dans une liste qui est basée sur le modèle. Par conséquent, ajoutez le code à la méthode de création qui ajoute de nouvelles données à une source de données. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Rubriques connexes
  
|Titre|Description|  
|-----------|-----------------|  
|[Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)|Montre comment créer un modèle ou de l’importer un modèle que vous exportez à partir de SharePoint.|  
|[Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)|Explique comment concevoir les éléments d’un modèle à l’aide des outils de conception de Visual Studio.|  
|[Quand utiliser SharePoint Designer vs. Solutions de Visual Studio lors de la création à l’aide de BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Vous permet de décider s’il faut utiliser Visual Studio ou utiliser SharePoint Designer pour créer un modèle pour le BDC.|  
