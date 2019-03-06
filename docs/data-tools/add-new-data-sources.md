---
title: Ajouter de nouvelles sources de données
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 05a07fc3cb72f923d28ff907c9aec69620cbd40d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955802"
---
# <a name="add-new-data-sources"></a>Ajouter de nouvelles sources de données

Dans le contexte de .NET data tools dans Visual Studio, le terme *source de données* fait référence aux objets .NET qui se connectent à un magasin de données et rendre les données disponibles à une application .NET. Les concepteurs de Visual Studio peuvent consommer la sortie de la source de données pour générer le code réutilisable qui lie les données aux formulaires lorsque vous glissez -déplacez des objets de base de données à partir de la **des Sources de données** fenêtre. Ce type de source de données peut être :

- Une classe dans un modèle Entity Framework qui est associé à un type de base de données.

- Un jeu de données qui est associé à un type de base de données.

- Une classe qui représente un service réseau comme un service de données de Windows Communication Foundation (WCF) ou un service REST.

- Une classe qui représente un service SharePoint.

- Une classe ou une collection dans votre solution.

> [!NOTE]
> Si vous n’utilisez pas de fonctionnalités de liaison de données, jeux de données, Entity Framework, LINQ to SQL, WCF ou SharePoint, le concept de « data source » ne s’applique pas. Connectez-vous directement à la base de données en utilisant les objets SQLCommand simplement et communiquer directement avec la base de données.

Vous créez et modifiez des sources de données à l’aide de la **Assistant de Configuration de Source de données** dans une application Windows Forms ou Windows Presentation Foundation. Pour Entity Framework, commencez par créer vos classes d’entité, puis démarrer l’Assistant en sélectionnant **projet** > **ajouter une nouvelle Source de données** (décrite plus en détail plus loin dans cet article).

![Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Fenêtre Sources de données

Après avoir créé une source de données, il apparaît dans le **des Sources de données** fenêtre outil.

> [!TIP]
> Pour ouvrir le **des Sources de données** fenêtre, assurez-vous que votre projet est ouvert, puis appuyez sur **MAJ**+**Alt**+**D**ou choisissez **vue** > **Windows autres** > **des Sources de données**.

Vous pouvez faire glisser une source de données à partir de la **des Sources de données** fenêtre sur une aire de conception de formulaire ou d’un contrôle. Cela entraîne la génération d’un code réutilisable qui affiche les données à partir du magasin de données.

L’illustration suivante montre un jeu de données qui a été supprimé sur un formulaire Windows. Si vous sélectionnez **F5** sur l’application, les données à partir de la base de données sous-jacente s’affichent dans les contrôles du formulaire.

![Opération de glisser de Source de données](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Source de données pour une base de données ou un fichier de base de données

Vous pouvez créer un jeu de données ou un modèle Entity Framework à utiliser comme source de données pour une base de données ou d’un fichier de base de données.

### <a name="dataset"></a>Groupe de données

Pour créer un jeu de données comme source de données, exécutez le **Assistant de Configuration de Source de données** en sélectionnant **projet** > **ajouter une nouvelle Source de données**. Choisissez le **base de données** source de données tapez, puis suivez les invites pour spécifier une connexion de base de données nouvelle ou existante, ou d’un fichier de base de données.

### <a name="entity-classes"></a>Classes Entity

Pour créer un modèle Entity Framework comme source de données :

1. Exécutez le **Assistant Entity Data Model** pour créer les classes d’entité. Sélectionnez **projet** > **ajouter un nouvel élément** > **ADO.NET Entity Data Model**.

   ![Nouvel élément de projet de modèle Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Choisissez la méthode que vous souhaitez générer le modèle par.

   ![Entity Data Model (assistant)](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Ajouter le modèle comme source de données. Les classes générées s’affichent dans le **Assistant de Configuration de Source de données** lorsque vous choisissez la **objets** catégorie.

   ![Assistant de Configuration de Source de données avec les Classes d’entité](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Source de données pour un service

Pour créer une source de données à partir d’un service, exécutez le **Assistant de Configuration de Source de données** et choisissez le **Service** type de source de données. Il s’agit simplement d’un raccourci vers le **ajouter une référence de Service** boîte de dialogue, vous pouvez également accéder en double-cliquant sur le projet dans **l’Explorateur de solutions** et en sélectionnant **ajouter une référence de service**.

Lorsque vous créez une source de données à partir d’un service, Visual Studio ajoute une référence de service à votre projet. Visual Studio crée également des objets proxy qui correspondent aux objets retournées par le service. Par exemple, un service qui retourne un jeu de données est représenté dans votre projet comme un jeu de données ; un service qui retourne qu'un type spécifique est représenté dans votre projet en tant que le type retourné.

Vous pouvez créer une source de données parmi les types de services suivants :

- [Services de données WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Services WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Services web

    > [!NOTE]
    > Les éléments qui apparaissent dans le **des Sources de données** fenêtre sont dépendants des données retournées par le service. Certains services peuvent ne pas fournir suffisamment d’informations pour que l’**Assistant Configuration de source de données** puisse créer des objets pouvant être liés. Par exemple, si le service retourne un dataset non typé, aucun élément ne s’affichent dans le **des Sources de données** fenêtre lorsque vous terminez l’Assistant. Il s’agit, car les datasets non typés ne fournissent pas un schéma, et par conséquent, l’Assistant n’a pas suffisamment d’informations pour créer la source de données.

## <a name="data-source-for-an-object"></a>Source de données pour un objet

Vous pouvez créer une source de données à partir de n’importe quel objet qui expose une ou plusieurs propriétés publiques en exécutant la **Assistant de Configuration de Source de données** , puis en sélectionnant le **objet** type de source de données. Toutes les propriétés publiques d’un objet sont affichées dans le **des Sources de données** fenêtre. Si vous utilisez Entity Framework et que vous avez généré un modèle, il s’agit où vous trouvez les classes d’entité qui sont des sources de données pour votre application.

Sur le **sélectionner les objets de données** page, développez les nœuds dans l’arborescence pour localiser les objets que vous souhaitez lier à. L’arborescence contient des nœuds pour votre projet et pour les assemblys et d’autres projets qui sont référencés par votre projet.

Si vous souhaitez lier à un objet dans un assembly ou un projet qui n’apparaît pas dans l’arborescence, cliquez sur **ajouter une référence** et utiliser le **boîte de dialogue Ajouter une référence** pour ajouter une référence à l’assembly ou le projet. Après avoir ajouté la référence, l’assembly ou le projet est ajouté à l’arborescence.

> [!NOTE]
> Vous devrez peut-être générer le projet qui contient vos objets avant les objets s’affichent dans l’arborescence.

> [!NOTE]
> Pour prendre en charge de liaison de données de glisser-déplacer, des objets qui implémentent le <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource> interface doit avoir un constructeur par défaut. Sinon, Visual Studio ne peut pas instancier l’objet de source de données, et une erreur s’affiche lorsque vous faites glisser l’élément vers l’aire de conception.

## <a name="data-source-for-a-sharepoint-list"></a>Source de données pour une liste SharePoint

Vous pouvez créer une source de données à partir d’une liste SharePoint en exécutant la **Assistant de Configuration de Source de données** et en sélectionnant le **SharePoint** type de source de données. SharePoint expose des données via WCF Data Services, afin de la création d’une source de données SharePoint est identique à la création d’une source de données à partir d’un service. En sélectionnant le **SharePoint** d’élément dans le **Assistant de Configuration de Source de données** ouvre le **ajouter une référence de Service** boîte de dialogue, où vous vous connectez au service de données SharePoint en pointant sur le serveur SharePoint. Cela requiert le SDK SharePoint.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)