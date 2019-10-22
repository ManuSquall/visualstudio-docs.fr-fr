---
title: Enregistrer des données dans une base de données (plusieurs tables) | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655462"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Enregistrer des données dans une base de données (plusieurs tables)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'un des scénarios les plus courants dans le développement d'applications consiste à afficher des données dans un formulaire d'une application Windows, à modifier ces données, puis à renvoyer les données mises à jour à la base de données. Cette procédure pas à pas crée un formulaire affichant les données de deux tables associées et indique comment modifier les enregistrements et enregistrer les modifications dans la base de données. Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind.

 Vous pouvez enregistrer des données de votre application dans la base de données en appelant la méthode `Update` d'un TableAdapter. Lorsque vous faites glisser des tables depuis la fenêtre **sources de données** vers un formulaire, le code requis pour enregistrer les données est automatiquement ajouté. Toutes les tables supplémentaires ajoutées à un formulaire nécessitent l’ajout manuel de ce code. Cette procédure pas à pas indique comment ajouter du code pour enregistrer les mises à jour de plusieurs tables.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide en fonction de vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Paramètres Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création d’un projet d' **application Windows** .

- Création et configuration d’une source de données dans votre application à l’aide de l' [Assistant Configuration de source de données](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Définition des contrôles des éléments dans la [fenêtre sources de données](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Création de contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.

- Modification de quelques enregistrements dans chaque table du DataSet.

- Modification du code pour renvoyer les données mises à jour dans le dataset à la base de données.

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- avoir accès à l'exemple de base de données Northwind.

## <a name="create-the-windows-application"></a>Créer l’application Windows
 La première étape consiste à créer une **application Windows**. L’attribution d’un nom au projet est facultative au cours de cette étape, mais nous allons lui donner un nom, car nous envisageons de l’enregistrer ultérieurement.

#### <a name="to-create-the-new-windows-application-project"></a>Pour créer le projet d’application Windows

1. Dans le menu **fichier** , créez un nouveau projet.

2. Attribuez un nom au projet `UpdateMultipleTablesWalkthrough`.

3. Sélectionnez **application Windows**, puis cliquez sur **OK**. Pour plus d’informations, consultez [applications clientes](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Le projet **UpdateMultipleTablesWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-the-data-source"></a>Créer la source de données
 Cette étape crée une source de données à partir de la base de données Northwind à l’aide de l’**Assistant Configuration de source de données**. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Dans le menu **données** , sélectionnez**afficher les sources de données**.

2. Dans la fenêtre **sources de données** , sélectionnez Ajouter une**nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

3. Dans l’écran **choisir un type de source de données**, sélectionnez **base de**données, puis sélectionnez **suivant**.

4. Dans l’écran **choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         ou

    - Sélectionnez **Nouvelle connexion** pour ouvrir la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option permettant d’inclure des données sensibles, puis sélectionnez **suivant**.

6. Dans la **chaîne de connexion enregistrer dans le fichier de configuration de l’application**, sélectionnez **suivant**.

7. Dans l’écran **choisir vos objets de base de données**, développez le nœud **tables** .

8. Sélectionnez les tables **Customers** et **Orders** , puis sélectionnez **Finish**.

     **NorthwindDataSet** est ajouté à votre projet et les tables apparaissent dans la fenêtre **Sources de données**.

## <a name="set-the-controls-to-be-created"></a>Définir les contrôles à créer
 Pour cette procédure pas à pas, les données de la table `Customers` sont dans une disposition des **Détails** où les données sont affichées dans des contrôles individuels. Les données de la table `Orders` sont dans une disposition en **grille** qui est affichée dans un contrôle <xref:System.Windows.Forms.DataGridView>.

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Pour définir le type de déplacement des éléments de la fenêtre Sources de données

1. Dans la fenêtre **sources de données** , développez le nœud **Customers** .

2. Sur le nœud **Customers** , sélectionnez **Details** dans la liste de contrôle pour remplacer le contrôle de la table **Customers** par des contrôles individuels. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Créer le formulaire lié aux données
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire

1. Faites glisser le nœud **Customers** depuis la fenêtre **Sources de données** vers **Form1**.

     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

2. Faites glisser le nœud **Orders** associé depuis la fenêtre **Sources de données** vers **Form1**.

    > [!NOTE]
    > Le nœud **Orders** associé est situé sous la colonne **Fax** et constitue un nœud enfant du nœud **Customers**.

     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. Un OrdersTableAdapter et <xref:System.Windows.Forms.BindingSource> apparaissent dans la barre d’état des composants.

## <a name="addcode-to-update-the-database"></a>Addcode pour mettre à jour la base de données
 Vous pouvez mettre à jour la base de données en appelant les méthodes `Update` des TableAdapters **Customers** et **Orders**. Par défaut, un gestionnaire d’événements pour le bouton **Enregistrer** de l' <xref:System.Windows.Forms.BindingNavigator> est ajouté au code du formulaire pour envoyer des mises à jour à la base de données. Cette procédure modifie le code pour envoyer les mises à jour dans le bon ordre. Cela élimine la possibilité de déclencher des erreurs d’intégrité référentielle. Le code implémente également la gestion des erreurs en enveloppant l'appel de mise à jour dans un bloc try-catch. Vous pouvez modifier le code pour répondre aux besoins de votre application.

> [!NOTE]
> Par souci de clarté, cette procédure pas à pas n’utilise pas de transaction. Toutefois, si vous mettez à jour au moins deux tables associées, vous devez inclure toute la logique de mise à jour dans une transaction. Une transaction est un processus qui garantit que toutes les modifications associées à une base de données réussissent avant que les modifications ne soient validées. Pour plus d’informations, consultez [transactions et accès concurrentiel](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).

#### <a name="to-add-update-logic-to-the-application"></a>Pour ajouter une logique de mise à jour à l'application

1. Sélectionnez le bouton **Enregistrer** dans la <xref:System.Windows.Forms.BindingNavigator>. l’éditeur de code s’ouvre dans le gestionnaire d’événements `bindingNavigatorSaveItem_Click`.

2. Remplacez le code dans le gestionnaire d'événements pour appeler les méthodes `Update` des TableAdapters associés. Le code suivant crée d'abord trois tables de données temporaires pour contenir les informations mises à jour pour chaque <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> et <xref:System.Data.DataRowState>). Les mises à jour sont ensuite exécutées dans le bon ordre. Le code doit se présenter comme suit :

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Tester l’application

#### <a name="to-test-the-application"></a>Pour tester l'application

1. Sélectionnez **F5**.

2. Apportez quelques modifications aux données d'un ou plusieurs enregistrements dans chaque table.

3. Sélectionnez le bouton **Enregistrer**.

4. Vérifiez les valeurs figurant dans la base de données pour confirmer que les modifications ont bien été enregistrées.

## <a name="next-steps"></a>Étapes suivantes
 Selon les exigences de votre application, vous pouvez effectuer plusieurs étapes après la création d’un formulaire lié aux données dans votre application Windows. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

- Ajout d'une fonctionnalité de recherche au formulaire. Pour plus d’informations, consultez [Comment : ajouter une requête paramétrable à une Application Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Modification de la source de données dans le but d'ajouter ou de supprimer des objets de base de données. Pour plus d’informations, consultez [Comment : modifier un DataSet](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
