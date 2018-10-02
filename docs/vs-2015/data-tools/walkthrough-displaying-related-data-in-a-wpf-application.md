---
title: 'Procédure pas à pas : Affichage de données liées dans une Application WPF | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f6a052f7894c37e35defc748528b01124957cbc6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494486"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Procédure pas à pas : affichage de données connexes dans une application WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer une application WPF qui affiche les données des tables de base de données qui ont une relation parent/enfant. Les données sont encapsulées dans des entités dans un Entity Data Model. L’entité parente contient des informations de vue d’ensemble pour un ensemble de commandes. Chaque propriété de cette entité est liée à un autre contrôle dans l’application. L’entité enfant contient des détails pour chaque commande. Ce jeu de données est lié à un <xref:System.Windows.Controls.DataGrid> contrôle.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une application WPF et Entity Data Model qui est généré à partir des données dans la base de données AdventureWorksLT.  
  
-   Création d’un ensemble de contrôles liés aux données qui affichent des informations de vue d’ensemble pour un ensemble de commandes. Vous créez les contrôles en faisant glisser une entité parente à partir de la **des Sources de données** fenêtre à **le Concepteur WPF**.  
  
-   Création d’un <xref:System.Windows.Controls.DataGrid> contrôle qui affiche des détails connexes pour chaque sélectionné ordre. Vous créez les contrôles en faisant glisser une entité enfant à partir de la **des Sources de données** fenêtre dans une fenêtre de **le Concepteur WPF**.  
  
     [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT. Vous pouvez télécharger la base de données AdventureWorksLT à partir de la [site CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :  
  
-   Entity Data Models et ADO.NET Entity Framework. Pour plus d’informations, consultez [présentation d’Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
-   Utilisation du Concepteur WPF. Pour plus d’informations, consultez [WPF et Silverlight Designer Overview](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Liaison de données WPF. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Création du projet  
 Créer un projet WPF pour afficher les enregistrements de commande.  
  
#### <a name="to-create-a-new-wpf-project"></a>Pour créer un projet WPF  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Windows**.  
  
4.  Assurez-vous que l’option **.NET Framework 4** est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue. Le <xref:System.Windows.Controls.DataGrid> contrôle que vous utilisez dans cette procédure pas à pas est disponible uniquement dans le .NET Framework 4.  
  
5.  Sélectionnez le **Application WPF** modèle de projet.  
  
6.  Dans la zone **Nom**, tapez `AdventureWorksOrdersViewer`.  
  
7.  Cliquez sur **OK**.  
  
     Visual Studio crée le `AdventureWorksOrdersViewer` projet.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Création d’un Entity Data Model pour l’Application  
 Avant de pouvoir créer des contrôles liés aux données, vous devez définir un modèle de données pour votre application et l’ajouter à la **des Sources de données** fenêtre. Dans cette procédure pas à pas, le modèle de données est un Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>Pour créer un Entity Data Model  
  
1.  Sur le **données** menu, cliquez sur **ajouter une nouvelle Source de données** pour ouvrir le **Assistant de Configuration de Source de données**.  
  
2.  Sur le **choisir un Type de Source de données** , cliquez sur **base de données**, puis cliquez sur **suivant**.  
  
3.  Sur le **choisir un modèle de base de données** , cliquez sur **Entity Data Model**, puis cliquez sur **suivant**.  
  
4.  Sur le **choisir le contenu du modèle** , cliquez sur **générer à partir de la base de données**, puis cliquez sur **suivant**.  
  
5.  Sur le **choisir votre connexion de données** page, effectuez l’une des opérations suivantes :  
  
    -   Si une connexion de données à l’exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la.  
  
         - ou -  
  
    -   Cliquez sur **nouvelle connexion** et créer une connexion à la base de données AdventureWorksLT.  
  
     Assurez-vous que le **enregistrer des paramètres de connexion entity dans App.Config en tant que** option est sélectionnée, puis cliquez sur **suivant**.  
  
6.  Sur le **choisir vos objets de base de données** page, développez **Tables**, puis sélectionnez les tables suivantes :  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  Cliquez sur **Terminer**.  
  
8.  Générez le projet.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Lié aux données de création de contrôles qui affichent les commandes  
 Créer des contrôles qui affichent des enregistrements de commande en faisant glisser le `SalesOrderHeaders` entité à partir de la **des Sources de données** fenêtre vers le Concepteur WPF.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Pour créer des contrôles liés aux données qui affichent les enregistrements de commande  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur MainWindow.xaml.  
  
     La fenêtre s'ouvre dans le Concepteur WPF.  
  
2.  Modifier le XAML afin que la **hauteur** et **largeur** propriétés sont définies à 800  
  
3.  Dans le **des Sources de données** fenêtre, cliquez sur le menu déroulant pour le **SalesOrderHeaders** nœud et sélectionnez **détails**.  
  
4.  Développez le **SalesOrderHeaders** nœud.  
  
5.  Cliquez sur le menu déroulant en regard **SalesOrderID** et sélectionnez **ComboBox**.  
  
6.  Pour chacun des nœuds enfants suivants de la **SalesOrderHeaders** nœud, cliquez sur le menu déroulant ensuite le nœud et sélectionnez **aucun**:  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **Sous-total**  
  
    -   **TaxAmt**  
  
    -   **Frais de transport**  
  
    -   **ROWGUID**  
  
    -   **ModifiedDate**  
  
     Cette action empêche Visual Studio de créer des contrôles liés aux données pour ces nœuds à l'étape suivante. Pour cette procédure pas à pas, il est supposé que l'utilisateur final n'a pas besoin d'afficher ces données.  
  
7.  À partir de la **des Sources de données** fenêtre, faites glisser le **SalesOrderHeaders** nœud dans la fenêtre de **le Concepteur WPF**.  
  
     Visual Studio génère le XAML qui crée un ensemble de contrôles liés aux données dans le **SalesOrderHeaders** entité et le code qui charge les données. Pour plus d’informations sur le XAML et le code généré, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8.  Dans le concepteur, cliquez sur la zone de liste déroulante en regard du **Sales Order ID** étiquette.  
  
9. Dans le **propriétés** fenêtre, sélectionnez la case à cocher à côté du **IsReadOnly** propriété.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Création d’un contrôle DataGrid qui affiche les détails de commande  
 Créer un <xref:System.Windows.Controls.DataGrid> contrôle qui affiche les détails de la commande en faisant glisser le `SalesOrderDetails` entité à partir de la **des Sources de données** fenêtre vers le Concepteur WPF.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Pour créer un contrôle DataGrid qui affiche les détails de commande  
  
1.  Dans le **des Sources de données** fenêtre, recherchez le **SalesOrderDetails** nœud qui est un enfant de la **SalesOrderHeaders** nœud.  
  
    > [!NOTE]
    >  Il existe également un **SalesOrderDetails** nœud qui est un homologue de la **SalesOrderHeaders** nœud. Assurez-vous que vous sélectionnez le nœud enfant de la **SalesOrderHeaders** nœud.  
  
2.  Développez l’enfant **SalesOrderDetails** nœud.  
  
3.  Pour chacun des nœuds enfants suivants de la **SalesOrderDetails** nœud, cliquez sur le menu déroulant ensuite le nœud et sélectionnez **aucun**:  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **ROWGUID**  
  
    -   **ModifiedDate**  
  
     Cette action empêche Visual Studio d’inclure ces données dans le <xref:System.Windows.Controls.DataGrid> contrôle que vous créez à l’étape suivante. Pour cette procédure pas à pas, il est supposé que l'utilisateur final n'a pas besoin d'afficher ces données.  
  
4.  À partir de la **des Sources de données** fenêtre, faites glisser l’enfant **SalesOrderDetails** nœud dans la fenêtre de **le Concepteur WPF**.  
  
     Visual Studio génère du XAML pour définir un nouveau lié aux données <xref:System.Windows.Controls.DataGrid> contrôle et le contrôle s’affiche dans le concepteur. Visual Studio met également à jour le texte généré `GetSalesOrderHeadersQuery` méthode dans le fichier code-behind pour inclure les données dans le **SalesOrderDetails** entité.  
  
## <a name="testing-the-application"></a>Test de l'application  
 Générez et exécutez l’application pour vérifier qu’il affiche les enregistrements de commande.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur **F5**.  
  
     L'application se génère et s'exécute. Vérifiez ce qui suit :  
  
    -   Le **Sales Order ID** zone de liste déroulante affiche **71774**. Il s’agit de l’ID de la première commande dans l’entité.  
  
    -   Pour chaque commande que vous sélectionnez dans la **Sales Order ID** zone de liste modifiable, les informations de commande détaillées sont affichées dans le <xref:System.Windows.Controls.DataGrid>.  
  
2.  Fermez l'application.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir effectué cette procédure pas à pas, découvrez comment utiliser le **des Sources de données** contrôle de fenêtre dans Visual Studio pour créer une liaison WPF à d’autres types de sources de données. Pour plus d’informations, consultez [WPF de lier des contrôles à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) et [WPF de lier des contrôles à un jeu de données](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Afficher des données associées dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)