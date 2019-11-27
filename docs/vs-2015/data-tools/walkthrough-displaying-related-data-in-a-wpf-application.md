---
title: 'Procédure pas à pas : affichage de données connexes dans une application WPF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 787be52eeb546d2ab184a172464862d10cb43288
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299579"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Procédure pas à pas : affichage de données connexes dans une application WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer une application WPF qui affiche des données de tables de base de données qui ont une relation parent/enfant. Les données sont encapsulées dans les entités d’un Entity Data Model. L’entité parente contient des informations générales sur un ensemble de commandes. Chaque propriété de cette entité est liée à un contrôle différent dans l’application. L’entité enfant contient des détails pour chaque commande. Ce jeu de données est lié à un contrôle de <xref:System.Windows.Controls.DataGrid>.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une application WPF et d’un Entity Data Model généré à partir des données de l’exemple de base de données AdventureWorksLT.

- Création d’un jeu de contrôles liés aux données qui affichent des informations de vue d’ensemble pour un ensemble de commandes. Vous créez les contrôles en faisant glisser une entité parente de la fenêtre **sources de données** vers **le Concepteur WPF**.

- Création d’un contrôle de <xref:System.Windows.Controls.DataGrid> qui affiche les détails associés pour chaque commande sélectionnée. Vous créez les contrôles en faisant glisser une entité enfant de la fenêtre **sources de données** vers une fenêtre du **Concepteur WPF**.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT. Vous pouvez télécharger la base de données AdventureWorksLT à partir du [site Web CodePlex](https://go.microsoft.com/fwlink/?linkid=87843).

  La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :

- Entity Data Models et ADO.NET Entity Framework. Pour plus d’informations, consultez [Entity Framework vue d’ensemble](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Utilisation du Concepteur WPF. Pour plus d’informations, consultez [vue d’ensemble de WPF et du Concepteur Silverlight](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Liaison de données WPF. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Création du projet
 Créez un projet WPF pour afficher les enregistrements de commande.

#### <a name="to-create-a-new-wpf-project"></a>Pour créer un projet WPF

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Développez  **C# Visual** ou **Visual Basic**, puis sélectionnez **Windows**.

4. Assurez-vous que **.NET Framework 4** est sélectionné dans la zone de liste déroulante en haut de la boîte de dialogue. Le contrôle <xref:System.Windows.Controls.DataGrid> que vous utilisez dans cette procédure pas à pas est uniquement disponible dans le .NET Framework 4.

5. Sélectionnez le modèle de projet **Application WPF**.

6. Dans la zone **Nom**, tapez `AdventureWorksOrdersViewer`.

7. Cliquez sur **OK**.

     Visual Studio crée le projet `AdventureWorksOrdersViewer`.

## <a name="creating-an-entity-data-model-for-the-application"></a>Création d’un Entity Data Model pour l’application
 Avant de pouvoir créer des contrôles liés aux données, vous devez définir un modèle de données pour votre application et l’ajouter à la fenêtre **Sources de données**. Dans cette procédure pas à pas, le modèle de données est un Entity Data Model.

#### <a name="to-create-an-entity-data-model"></a>Pour créer un Entity Data Model

1. Dans le menu **données** , cliquez sur **Ajouter une nouvelle source de données** pour ouvrir l' **Assistant Configuration de source de données**.

2. Dans la page **choisir un type de source de données** , cliquez sur **base de données**, puis sur **suivant**.

3. Dans la page **choisir un modèle de base de données** , cliquez sur **Entity Data Model**, puis cliquez sur **suivant**.

4. Dans la page **choisir le contenu du modèle** , cliquez sur **générer à partir de la base de données**, puis cliquez sur **suivant**.

5. Dans la page **choisir votre connexion de données** , effectuez l’une des opérations suivantes :

   - Si une connexion de données à l'exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la.

      -ou-

   - Cliquez sur **nouvelle connexion** et créez une connexion à la base de données AdventureWorksLT.

     Assurez-vous que l’option **enregistrer les paramètres de connexion de l’entité dans App. config en tant que** est sélectionnée, puis cliquez sur **suivant**.

6. Dans la page **choisir vos objets de base de données** , développez **tables**, puis sélectionnez les tables suivantes :

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. Cliquez sur **Terminer**.

8. créer le projet ;

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Création de contrôles liés aux données qui affichent les commandes
 Créez des contrôles qui affichent les enregistrements de commande en faisant glisser l’entité `SalesOrderHeaders` de la fenêtre **sources de données** vers le Concepteur WPF.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Pour créer des contrôles liés aux données qui affichent les enregistrements de commande

1. Dans **Explorateur de solutions**, double-cliquez sur MainWindow. Xaml.

    La fenêtre s'ouvre dans le Concepteur WPF.

2. Modifiez le code XAML afin que les propriétés **Height** et **Width** aient la valeur 800

3. Dans la fenêtre **sources de données** , cliquez sur le menu déroulant du nœud **SalesOrderHeaders** et sélectionnez **Détails**.

4. Développez le nœud **SalesOrderHeaders**.

5. Cliquez sur le menu déroulant en regard de **SalesOrderID** et sélectionnez **ComboBox**.

6. Pour chacun des nœuds enfants suivants du nœud **SalesOrderHeaders** , cliquez sur le menu déroulant en regard du nœud et sélectionnez **aucun**:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **Sous**

   - **TaxAmt**

   - **Fret**

   - **rowguid**

   - **ModifiedDate**

     Cette action empêche Visual Studio de créer des contrôles liés aux données pour ces nœuds à l'étape suivante. Pour cette procédure pas à pas, il est supposé que l'utilisateur final n'a pas besoin d'afficher ces données.

7. À partir de la fenêtre **sources de données** , faites glisser le nœud **SalesOrderHeaders** vers la fenêtre du **Concepteur WPF**.

    Visual Studio génère du code XAML qui crée un ensemble de contrôles liés aux données de l’entité **SalesOrderHeaders** , ainsi que le code qui charge les données. Pour plus d’informations sur le code XAML et le code générés, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. Dans le concepteur, cliquez sur la zone de liste déroulante en regard de l’étiquette de l' **ID de commande client** .

9. Dans la fenêtre **Propriétés**, cochez la case en regard de la propriété **IsReadOnly**.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Création d’un DataGrid qui affiche les détails de la commande
 Créez un contrôle de <xref:System.Windows.Controls.DataGrid> qui affiche les détails des commandes en faisant glisser l’entité `SalesOrderDetails` depuis la fenêtre **sources de données** vers le Concepteur WPF.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Pour créer un DataGrid qui affiche les détails de la commande

1. Dans la fenêtre **sources de données** , localisez le nœud **SalesOrderDetails** qui est un enfant du nœud **SalesOrderHeaders** .

   > [!NOTE]
   > Il existe également un nœud **SalesOrderDetails** qui est un homologue du nœud **SalesOrderHeaders** . Veillez à sélectionner le nœud enfant du nœud **SalesOrderHeaders** .

2. Développez le nœud **SalesOrderDetails** enfant.

3. Pour chacun des nœuds enfants suivants du nœud **SalesOrderDetails** , cliquez sur le menu déroulant en regard du nœud et sélectionnez **aucun**:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **rowguid**

   - **ModifiedDate**

     Cette action empêche Visual Studio d’inclure ces données dans le contrôle de <xref:System.Windows.Controls.DataGrid> que vous créez à l’étape suivante. Pour cette procédure pas à pas, il est supposé que l'utilisateur final n'a pas besoin d'afficher ces données.

4. À partir de la fenêtre **sources de données** , faites glisser le nœud **SalesOrderDetails** enfant vers la fenêtre du **Concepteur WPF**.

    Visual Studio génère du code XAML pour définir un nouveau contrôle de <xref:System.Windows.Controls.DataGrid> lié aux données, et le contrôle s’affiche dans le concepteur. Visual Studio met également à jour la méthode `GetSalesOrderHeadersQuery` générée dans le fichier code-behind pour inclure les données dans l’entité **SalesOrderDetails** .

## <a name="testing-the-application"></a>Test de l'application
 Générez et exécutez l’application pour vérifier qu’elle affiche les enregistrements de commande.

#### <a name="to-test-the-application"></a>Pour tester l'application

1. Appuyez sur **F5**.

     L'application se génère et s'exécute. Vérifiez ce qui suit :

    - La zone de liste déroulante **Sales Order ID** affiche **71774**. Il s’agit du premier ID de commande dans l’entité.

    - Pour chaque commande que vous sélectionnez dans la zone de liste déroulante **n ° de commande** , des informations détaillées sur les commandes s’affichent dans la <xref:System.Windows.Controls.DataGrid>.

2. Fermez l'application.

## <a name="next-steps"></a>Étapes suivantes
 À l’issue de cette procédure pas à pas, Découvrez comment utiliser la fenêtre **sources de données** dans Visual Studio pour lier des contrôles WPF à d’autres types de sources de données. Pour plus d’informations, consultez [lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) et [lier des contrôles WPF à un DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md).

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)