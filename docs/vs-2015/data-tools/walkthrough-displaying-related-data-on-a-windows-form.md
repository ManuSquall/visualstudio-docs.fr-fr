---
title: 'Procédure pas à pas : Affichage de données liées sur un formulaire Windows | Microsoft Docs'
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: be86fa89cd35ff55ed9e454c9453b4d2684f311d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507687"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Procédure pas à pas : affichage de données liées sur un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans de nombreux scénarios d'application, vous voulez utiliser des données provenant de plusieurs tables et, souvent, des données provenant des tables associées. En d'autres termes, vous voulez utiliser une relation parent-enfant. Par exemple, vous voulez créer un formulaire qui affiche les commandes d'un client quand vous sélectionnez l'enregistrement de ce client spécifique. Vous affichez les enregistrements associés dans le formulaire en définissant la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> du <xref:System.Windows.Forms.BindingSource> enfant sur le <xref:System.Windows.Forms.BindingSource> parent (et non la table enfant), et en définissant la propriété <xref:System.Windows.Forms.BindingSource.DataMember%2A> du <xref:System.Windows.Forms.BindingSource> enfant sur la relation de données qui relie les tables parent et enfant.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un **Windows Application** projet.  
  
-   Création et configuration d’un jeu de données dans votre application selon le `Customers` et `Orders` tables dans la base de données Northwind à l’aide du [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Ajout de contrôles pour afficher des données de la table `Customers`.  
  
-   Ajout de contrôles pour afficher les `Orders` en fonction du `Customer` sélectionné.  
  
-   Test de l'application en sélectionnant différents clients et en vérifiant que les commandes appropriées sont affichées pour le client sélectionné.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind. Pour configurer des bases de données, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer un **Windows Application**.  
  
#### <a name="to-create-the-windows-application-project"></a>Pour créer le projet d'application Windows  
  
1.  À partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Attribuez un nom au projet `RelatedDataWalkthrough`.  
  
3.  Sélectionnez **Windows Application** et cliquez sur **OK**. Pour plus d’informations, consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Le **RelatedDataWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="creating-the-data-source"></a>Création de la source de données  
 Cette étape crée un dataset basé sur les tables `Customers` et `Orders` de l'exemple de base de données Northwind.  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.  
  
4.  Sur le **choisir votre connexion de données** page, procédez comme suit :  
  
    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.  
  
         - ou -  
  
    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **suivant**.  
  
6.  Cliquez sur **suivant** sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** page.  
  
7.  Développez le **Tables** nœud sur le **choisir vos objets de base de données** page.  
  
8.  Sélectionnez le **clients** et **commandes** tables, puis cliquez sur **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le **clients** table s’affiche dans le **des Sources de données** fenêtre.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Création de contrôles permettant d'afficher des données de la table Customers  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Pour créer des contrôles afin d'afficher les données des clients (enregistrements parents)  
  
1.  Dans le **des Sources de données** fenêtre, sélectionnez le **clients** de table, puis cliquez sur la flèche déroulante.  
  
2.  Choisissez **détails** dans le menu.  
  
3.  Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre en haut de **Form1**.  
  
     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Création de contrôles permettant d'afficher des données de la table Orders  
 ![Fenêtre de Sources de données montrant la relation](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Pour créer des contrôles afin d'afficher les commandes de chaque client (enregistrements enfants)  
  
-   Dans le **des Sources de données** fenêtre, développez le **clients** nœud et sélectionnez la dernière colonne dans le **clients** table, qui est une manière extensible **commandes** nœud et faites-le glisser vers le bas de **Form1**.  
  
     Un <xref:System.Windows.Forms.DataGridView> est ajouté au formulaire et un nouveau <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) ainsi qu'un nouveau TableAdapter (`OrdersTableAdapter`) sont ajoutés à la barre d'état des composants.  
  
    > [!NOTE]
    >  Ouvrez le [fenêtre Propriétés](../ide/reference/properties-window.md) et sélectionnez le **OrdersBindingSource**. Examinez les propriétés <xref:System.Windows.Forms.BindingSource.DataSource%2A> et <xref:System.Windows.Forms.BindingSource.DataMember%2A> pour observer la manière dont la liaison de données est configurée pour afficher les enregistrements associés. Le <xref:System.Windows.Forms.BindingSource.DataSource%2A> est défini sur le`CustomersBindingSource` (le <xref:System.Windows.Forms.BindingSource> de la table parente), et non sur la table `Orders`. La propriété <xref:System.Windows.Forms.BindingSource.DataMember%2A> est définie sur `FK_Orders_Customers`, qui est le nom de l'objet <xref:System.Data.DataRelation> reliant les tables.  
  
## <a name="testing-the-application"></a>Test de l'application  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Sélectionnez différents clients à l’aide de la **CustomersBindingNavigator** pour vérifier les commandes correctes sont affichées dans le <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un formulaire maître/détail. Vous pouvez apporter à cette procédure pas à pas l'amélioration suivante :  
  
-   Filtrage des enregistrements `Customers` en ajoutant le paramétrage de la table `Customers`. Pour ce faire, sélectionnez n’importe quel contrôle qui affiche les données à partir de la `Customers` table, cliquez sur la balise active, puis choisissez **ajouter une requête**. Terminer la [boîte de dialogue Générateur de critères de recherche](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Pour plus d’informations, consultez [Comment : ajouter une requête paramétrable à une Application de formulaires Windows](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : afficher des connexes d’Application de données dans un Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Vue d’ensemble du composant BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [Vue d'ensemble du contrôle BindingNavigator](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)