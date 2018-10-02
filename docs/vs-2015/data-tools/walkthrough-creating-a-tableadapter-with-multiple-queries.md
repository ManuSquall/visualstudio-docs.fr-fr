---
title: 'Procédure pas à pas : Création d’un TableAdapter avec plusieurs requêtes | Microsoft Docs'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503800"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Procédure pas à pas : création d'un TableAdapter avec plusieurs requêtes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette procédure pas à pas, vous allez créer un TableAdapter dans un jeu de données à l’aide de la [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). La procédure pas à pas vous accompagne tout au long des processus de création d’une deuxième requête dans le [TableAdapter](../data-tools/tableadapter-overview.md) à l’aide de la [modification des TableAdapters](../data-tools/editing-tableadapters.md) au sein de la [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un nouveau **Windows Application** projet.  
  
-   Création et configuration d’une source de données dans votre application en générant un dataset avec le **Assistant de Configuration de Source de données**.  
  
-   Ouverture du nouveau dataset dans le **Concepteur de Dataset**.  
  
-   Ajout de requêtes au TableAdapter avec le **Assistant Configuration de requêtes TableAdapter**.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à l'exemple de base de données Northwind (vers SQL Server ou Access). Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Création d'une application Windows  
 La première étape consiste à créer une Application Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Pour créer le projet d'application Windows  
  
1.  Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], à partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Choisissez un langage de programmation dans le **Types de projets** volet.  
  
3.  Cliquez sur **Windows Application** dans le **modèles** volet.  
  
4.  Nommez le projet `TableAdapterQueriesWalkthrough`, puis cliquez sur **OK**.  
  
     Visual Studio ajoute le projet à **l’Explorateur de solutions** et affiche un nouveau formulaire dans le concepteur.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Création d'une source de données de base de données avec un TableAdapter  
 Cette étape crée une source de données à l’aide de la **Assistant de Configuration de Source de données** selon le `Customers` table dans la base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Sélectionnez le **clients** table, puis cliquez sur **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le **clients** table s’affiche dans le **des Sources de données** fenêtre.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Ouverture du dataset dans le Concepteur de DataSet  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Pour ouvrir le dataset dans le Concepteur de DataSet  
  
1.  Avec le bouton droit **NorthwindDataset** dans le **des Sources de données** fenêtre.  
  
2.  Dans le menu contextuel, choisissez **modifier le DataSet avec le concepteur**.  
  
     NorthwindDataset s’ouvre dans le **Concepteur de Dataset**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Ajout d'une deuxième requête au CustomersTableAdapter  
 L’Assistant a créé le jeu de données avec un **clients** table de données et **CustomersTableAdapter**. Cette section de la procédure pas à pas ajoute une deuxième requête à la **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>Pour ajouter une deuxième requête au CustomersTableAdapter  
  
1.  Faites glisser un **requête** à partir de la **DataSet** onglet de la **boîte à outils** sur le **clients** table.  
  
     Le [modification des TableAdapters](../data-tools/editing-tableadapters.md) s’ouvre.  
  
2.  Sélectionnez **utiliser des instructions SQL**, puis cliquez sur **suivant**.  
  
3.  Sélectionnez **LECT qui retourne des lignes**, puis cliquez sur **suivant**.  
  
4.  Ajoutez une clause WHERE à la requête pour obtenir ce qui suit :  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Si vous utilisez la version Access de Northwind, remplacez le @City paramètre avec un point d’interrogation. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  Sur le **choisir les méthodes à générer** page, nommez le **remplir un DataTable** méthode `FillByCity`.  
  
    > [!NOTE]
    >  La méthode à **retourner un DataTable** n’est pas utilisé dans cette procédure pas à pas, donc vous pouvez désactivez la case à cocher ou laissez le nom par défaut.  
  
6.  Cliquez sur **suivant** et terminez l’Assistant.  
  
     Le **FillByCity** requête est ajoutée à la **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Ajout de code pour exécuter la requête supplémentaire dans le formulaire  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
1.  Sélectionnez **Form1** dans **l’Explorateur de solutions**, puis cliquez sur **Concepteur de vues**.  
  
2.  Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre à **Form1**.  
  
3.  Passez au mode code en sélectionnant **Code** à partir de la **vue** menu.  
  
4.  Remplacez le code dans le gestionnaire d'événements `Form1_Load` par ce qui suit pour exécuter la requête `FillByCity`.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Exécution de l'application  
  
#### <a name="to-run-the-application"></a>Pour exécuter l'application  
  
-   Appuyez sur F5.  
  
-   La grille est remplie avec les clients dont la valeur `City` est `Seattle`.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
### <a name="to-add-functionality-to-your-application"></a>Pour ajouter une fonctionnalité à votre application  
  
-   Ajoutez des contrôles <xref:System.Windows.Forms.TextBox> et <xref:System.Windows.Forms.Button>, et passez la valeur de la zone de texte à la requête. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Ajoutez une logique de validation à l'événement <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> des tables de données du dataset. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)