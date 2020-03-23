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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302251"
---
# <a name="add-new-data-sources"></a>Ajouter de nouvelles sources de données

Dans le cadre des outils de données .NET dans Visual Studio, la source de *données* terme se réfère à des objets .NET qui se connectent à un magasin de données et de rendre les données disponibles à une application .NET. Les concepteurs de Visual Studio peuvent consommer la sortie de la source de données pour générer le code de la plaque chauffante qui lie les données aux formulaires lorsque vous faites glisser et larguer des objets de base de données à partir de la fenêtre **Data Sources.** Ce type de source de données peut être :

- Une classe dans un modèle de cadre d’entité qui est associée à une sorte de base de données.

- Un ensemble de données qui est associé à une sorte de base de données.

- Une classe qui représente un service réseau tel qu’un service de données de la Windows Communication Foundation (WCF) ou un service REST.

- Une classe qui représente un service SharePoint.

- Une classe ou une collection dans votre solution.

> [!NOTE]
> Si vous n’utilisez pas de fonctionnalités, de jeux de données, de cadre d’entité, de LINQ à SQL, WCF ou SharePoint, le concept de « source de données » ne s’applique pas. Il suffit de se connecter directement à la base de données en utilisant les objets SQLCommand et de communiquer directement avec la base de données.

Vous créez et modifiez des sources de données en utilisant le **Data Source Configuration Wizard** dans une application Windows Forms ou Windows Presentation Foundation. Pour Entity Framework, créez d’abord vos classes d’entités, puis commencez l’assistant en sélectionnant **Project** > **Add New Data Source** (décrit plus en détail plus tard dans cet article).

![Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Fenêtre Sources de données

Après avoir créé une source de données, il apparaît dans la fenêtre de l’outil **Sources de données.**

> [!TIP]
> Pour ouvrir la fenêtre **Data Sources,** assurez-vous que votre projet est ouvert, puis appuyez sur **Shift**+**Alt**+**D** ou choisissez **Voir** > **d’autres** > sources**de données**Windows .

Vous pouvez faire glisser une source de données de la fenêtre **Data Sources** sur une surface ou un contrôle de conception de formulaires. Cela provoque l’généré du code de la plaque chauffante qui affiche les données du magasin de données.

L’illustration suivante montre un jeu de données qui a été déposé sur un formulaire Windows. Si vous sélectionnez **F5** sur l’application, les données de la base de données sous-jacente apparaissent dans les contrôles du formulaire.

![Opération de traînée de source de données](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Source de données pour une base de données ou un fichier de base de données

Vous pouvez créer un jeu de données ou un modèle cadre d’entité à utiliser comme source de données pour une base de données ou un fichier de base de données.

### <a name="dataset"></a>Dataset

Pour créer un jeu de données en tant que source de données, exécutez le **Data Source Configuration Wizard** en sélectionnant **Project** > **Add New Data Source**. Choisissez le type de source de données **de base** de données et suivez les invites pour spécifier une nouvelle connexion de base de données ou existante, soit un fichier de base de données.

### <a name="entity-classes"></a>Classes Entity

Créer un modèle cadre d’entité comme source de données :

1. Exécutez **l’Assistant modèle de données d’entité** pour créer les classes d’entités. Sélectionnez **Projet** > **Ajouter un nouvel élément** > **ADO.NET modèle de données d’entité**.

   ![Nouvel élément de projet modèle de cadre d’entité](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Choisissez la méthode que vous voulez générer le modèle par.

   ![Entity Data Model (assistant)](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Ajoutez le modèle comme source de données. Les classes générées apparaissent dans le Magicien de configuration **de source de données** lorsque vous choisissez la catégorie **Objets.**

   ![Assistant de configuration de source de données avec des classes d’entités](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Source de données pour un service

Pour créer une source de données à partir d’un service, exécutez **l’assistant de configuration de source de données** et choisissez le type de source de données **service.** Il s’agit simplement d’un raccourci vers la boîte de dialogue **Add Service Reference,** à laquelle vous pouvez également accéder en cliquant à droite sur le projet dans **Solution Explorer** et en sélectionnant la référence de **service Add**.

Lorsque vous créez une source de données à partir d’un service, Visual Studio ajoute une référence de service à votre projet. Visual Studio crée également des objets proxy qui correspondent aux objets que le service retourne. Par exemple, un service qui renvoie un jeu de données est représenté dans votre projet sous forme d’ensemble de données; un service qui renvoie un type spécifique est représenté dans votre projet au fur et à mesure que le type est retourné.

Vous pouvez créer une source de données à partir des types de services suivants :

- [Services de données WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Services WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- SERVICES WEB

    > [!NOTE]
    > Les éléments qui apparaissent dans la fenêtre **Sources de données** dépendent des données que le service retourne. Certains services peuvent ne pas fournir suffisamment d’informations pour que l’**Assistant Configuration de source de données** puisse créer des objets pouvant être liés. Par exemple, si le service renvoie un jeu de données nontypé, aucun élément n’apparaît dans la fenêtre **Sources de données** lorsque vous terminez l’assistant. C’est parce que les jeux de données non cartographiques ne fournissent pas un schéma, et donc l’assistant n’a pas assez d’informations pour créer la source de données.

## <a name="data-source-for-an-object"></a>Source de données pour un objet

Vous pouvez créer une source de données à partir de n’importe quel objet qui expose une ou plusieurs propriétés publiques en exécutant le **Data Source Configuration Wizard,** puis en sélectionnant le type de source de données **d’objet.** Toutes les propriétés publiques d’un objet sont affichées dans la fenêtre **Data Sources.** Si vous utilisez Entity Framework et avez généré un modèle, c’est là que vous trouvez les classes d’entités qui sont les sources de données de votre application.

Sur la page **Sélectionner les objets de données,** étendre les nœuds dans la vue de l’arbre pour localiser les objets que vous souhaitez lier. La vue de l’arbre contient des nœuds pour votre projet et pour les assemblages et autres projets qui sont référencés par votre projet.

Si vous souhaitez vous lier à un objet dans un assemblage ou un projet qui n’apparaît pas dans la vue de l’arbre, cliquez sur **Ajouter la référence** et utilisez la boîte de dialogue de référence **Ajouter** pour ajouter une référence à l’assemblage ou au projet. Après avoir ajouté la référence, l’assemblage ou le projet est ajouté à la vue de l’arbre.

> [!NOTE]
> Vous devrez peut-être construire le projet qui contient vos objets avant que les objets n’apparaissent dans la vue de l’arbre.

> [!NOTE]
> Pour prendre en charge la liaison de <xref:System.ComponentModel.ITypedList> données <xref:System.ComponentModel.IListSource> de drag-and-drop, les objets qui implémentent l’interface ou l’interface doivent avoir un constructeur par défaut. Dans le cas contraire, Visual Studio ne peut pas instantanéiser l’objet source de données, et il affiche une erreur lorsque vous faites glisser l’élément à la surface de conception.

## <a name="data-source-for-a-sharepoint-list"></a>Source de données pour une liste SharePoint

Vous pouvez créer une source de données à partir d’une liste SharePoint en exécutant **l’assistant de configuration de source de données** et en sélectionnant le type de source de données **SharePoint.** SharePoint expose les données via WCF Data Services, de sorte que la création d’une source de données SharePoint est la même chose que la création d’une source de données à partir d’un service. La sélection de l’élément **SharePoint** dans le **Data Source Configuration Wizard** ouvre la boîte de dialogue Add Service **Reference,** où vous vous connectez au service de données SharePoint en pointant vers le serveur SharePoint. Cela nécessite le SharePoint SDK.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
