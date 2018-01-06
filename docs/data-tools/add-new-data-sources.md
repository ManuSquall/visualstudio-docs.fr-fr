---
title: "Ajouter de nouvelles sources de données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 865f575aefedb5813a72d7a0bb2024bc85313db0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="add-new-data-sources"></a>Ajouter de nouvelles sources de données
Dans le cadre des outils de données .NET dans Visual Studio, le terme *source de données* fait référence à des objets .NET qui se connectent à un magasin de données et exposent les données à une application .NET. Les concepteurs Visual Studio peuvent consommer la sortie de la source de données pour générer le code réutilisable qui lie les données aux formulaires lorsque vous glissez -déplacez des objets de base de données à partir de la **des Sources de données** fenêtre. Ce type de source de données peut être :  
  
-   Une classe dans un modèle Entity Framework qui est associé à un type de base de données.  
  
-   Un jeu de données qui est associé à un type de base de données.  
  
-   Une classe qui représente un service réseau comme un service de données de Windows Communication Foundation (WCF) ou un service REST.  
  
-   Une classe qui représente un service SharePoint.  
  
-   Une classe ou une collection dans votre solution.  
  
> [!NOTE]
>  Si vous n’utilisez pas les fonctionnalités de liaison de données, datasets, Entity Framework, LINQ to SQL, WCF ou SharePoint, le concept de « data source » ne s’applique pas. Connectez-vous directement à la base de données en utilisant les objets SQLCommand simplement et communiquer directement avec la base de données.  
  
 Vous créez et modifiez des sources de données à l’aide de la **Assistant de Configuration de Source de données** dans une application Windows Forms ou Windows Presentation Foundation. Entity Framework, tout d’abord créer vos classes d’entité, puis démarrez l’Assistant en sélectionnant **projet** > **ajouter une nouvelle Source de données** (décrite plus en détail plus loin dans cet article).  
  
 ![Assistant Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png "Assistant Configuration de Source de données")  
  
 Après avoir créé une source de données, il apparaît dans le **des Sources de données** fenêtre outil (Maj + Alt + D ou **vue** > **autres fenêtres**  >  **Source de données**). Vous pouvez faire glisser une source de données à partir de la **des Sources de données** fenêtre sur une aire de conception de formulaire ou un contrôle. Cela entraîne la génération de code réutilisable, le code qui affiche les données provenant de la banque de données à l’utilisateur. L’illustration suivante montre un jeu de données qui a été déposé sur un Windows form. Si vous avez sélectionné F5 sur l’application, les données à partir de la base de données sous-jacente apparaissent dans les contrôles du formulaire.  
  
 ![Opération de glissement de Source de données](../data-tools/media/raddata-data-source-drag-operation.png "opération de glissement de raddata Source de données")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Source de données pour une base de données ou un fichier de base de données  
  
### <a name="dataset"></a>Groupe de données  
 Pour créer un jeu de données comme source de données, exécutez le **Assistant de Configuration de Source de données** (**projet** > **ajouter une nouvelle Source de données**) et choisissez le  **Base de données** type de source de données. Suivez les invites pour spécifier une connexion de base de données nouvelle ou existante, ou un fichier de base de données.  
  
### <a name="entity-classes"></a>Classes d’entité  
 Pour créer un modèle Entity Framework en tant que source de données, exécutez d’abord la **Assistant Entity Data Model** pour créer les classes d’entité (**projet** > **ajouter un nouvel élément**  >  **ADO.NET Entity Data Model**).  
  
 ![Nouvel élément de projet de modèle Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "élément de projet de modèle de nouvelle Entity Framework raddata")  
  
 Choisissez la méthode par laquelle vous souhaitez générer le modèle.  
  
 ![Assistant Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "raddata Assistant Entity Data Model")  
  
 Ajouter le modèle comme source de données. Les classes qui ont été créés s’affichent dans le **Assistant de Configuration de Source de données** lorsque vous choisissez la **objets** catégorie.  
  
 ![Assistant de Configuration de Source de données avec les Classes d’entité](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata Assistant de Configuration de Source de données avec les Classes d’entité")  
  
## <a name="data-source-for-a-service"></a>Source de données pour un service  
 Pour créer une source de données à partir d’un service, exécutez le **Assistant de Configuration de Source de données** et choisissez la **Service** type de source de données. Il s’agit simplement d’un raccourci vers le **ajouter une référence de Service** boîte de dialogue, vous pouvez également accéder en cliquant sur le projet dans **l’Explorateur de solutions** et en sélectionnant **ajouter une référence de service** .  
  
 Lorsque vous créez une source de données à partir d’un service, Visual Studio ajoute une référence de service à votre projet. Visual Studio crée également des objets proxy qui correspondent aux objets que le service renvoie. Par exemple, un service qui retourne un jeu de données est représenté dans votre projet comme un jeu de données ; un service qui retourne qu'un type spécifique est représenté dans votre projet en tant que le type retourné.  
  
 Vous pouvez créer une source de données à partir des types de services suivants :  
  
-   Services de données WCF. Pour plus d’informations, consultez [vue d’ensemble](/dotnet/framework/data/wcf/wcf-data-services-overview).  
  
-   Services WCF. Pour plus d’informations, consultez [Services Windows Communication Foundation et Services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Services Web.  
  
    > [!NOTE]
    >  Les éléments qui apparaissent dans le **des Sources de données** sont dépendants des données retournées par le service. Certains services ne peuvent pas fournir suffisamment d’informations pour le **Assistant de Configuration de Source de données** pour créer des objets pouvant être liés. Par exemple, si le service retourne un dataset non typé, aucun élément ne s’affiche dans le **des Sources de données** fenêtre lorsque vous terminez l’Assistant. Il s’agit, car les datasets non typés ne fournissent pas d’un schéma, et par conséquent, l’Assistant n’a pas suffisamment d’informations pour créer la source de données.  
  
## <a name="data-source-for-an-object"></a>Source de données pour un objet  
 Vous pouvez créer une source de données à partir de n’importe quel objet qui expose une ou plusieurs propriétés publiques en exécutant le **Assistant de Configuration de Source de données** , puis en sélectionnant le **objet** type de source de données. Toutes les propriétés publiques d’un objet sont affichées dans le **des Sources de données** fenêtre.   Si vous utilisez Entity Framework et que vous avez généré un modèle, il s’agit où vous trouver les classes d’entité qui seront les sources de données pour votre application.  
  
 Sur le **sélectionner les objets de données** page, développez les nœuds dans l’arborescence pour localiser les objets que vous souhaitez lier. L’arborescence contient des nœuds pour votre projet et pour les assemblys et d’autres projets qui sont référencés par votre projet.  
  
 Si vous souhaitez lier à un objet dans un assembly ou un projet qui n’apparaît pas dans l’arborescence, cliquez sur **ajouter une référence** et utiliser le **boîte de dialogue Ajouter une référence** pour ajouter une référence à l’assembly ou le projet. Après avoir ajouté la référence, l’assembly ou le projet est ajouté à l’arborescence.  
  
> [!NOTE]
>  Vous devrez peut-être générer le projet qui contient vos objets avant que les objets apparaissent dans l’arborescence.  
  
> [!NOTE]
>  Pour prendre en charge de liaison de données par glisser-déplacer, des objets qui implémentent la <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource> interface doit avoir un constructeur par défaut. Sinon, Visual Studio ne peut pas instancier l’objet de source de données, et il affiche une erreur lorsque vous faites glisser l’élément vers l’aire de conception.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Source de données pour une liste SharePoint  
 Vous pouvez créer une source de données à partir d’une liste SharePoint en exécutant le **Assistant de Configuration de Source de données** et en sélectionnant le **SharePoint** type de source de données. SharePoint expose des données via [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], de sorte que la création d’une source de données SharePoint est identique à la création d’une source de données à partir d’un service. En sélectionnant le **SharePoint** d’élément dans le **Assistant de Configuration de Source de données** ouvre le **ajouter une référence de Service** boîte de dialogue, dans laquelle vous vous connectez au service de données SharePoint en pointant sur le serveur SharePoint.  Cela requiert le SDK SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)