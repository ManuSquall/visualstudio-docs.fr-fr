---
title: "Enregistrer les données avec le DBDirect du TableAdapter méthodes | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 3ed52a167b607236b8493e4c8c1736ee597162b9
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Enregistrer les données avec le DBDirect du TableAdapter méthodes
Cette procédure pas à pas fournit des instructions détaillées pour l’exécution des instructions SQL directement sur une base de données à l’aide des méthodes DBDirect d’un TableAdapter. Les méthodes DBDirect d’un TableAdapter fournissent un niveau de contrôle sur vos mises à jour de la base de données. Vous pouvez les utiliser pour exécuter des instructions SQL et les procédures stockées en appelant les `Insert`, `Update`, et `Delete` méthodes selon les besoins de votre application (par opposition à surchargées `Update` méthode qui effectue la mise à jour Instructions INSERT et DELETE dans un seul appel).  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Créer un nouveau **Application Windows Forms**.  
  
-   Créer et configurer un dataset avec le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Sélectionnez le contrôle à créer sur le formulaire lorsque vous faites glisser des éléments à partir de la **des Sources de données** fenêtre. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Créer un formulaire lié aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre sur le formulaire.  
  
-   Ajouter des méthodes pour accéder à la base de données directement et d’effectuer des insertions, mises à jour et suppressions...  
  
## <a name="prerequisites"></a>Conditions préalables  
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.  
  
1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement des éditions de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.  
  
2.  Installer la base de données Northwind en procédant comme suit :  

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .  

       Une fenêtre d’éditeur de requête s’ouvre.  

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.  

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.  

       Après une courte période, la requête est terminée et la base de données Northwind est créé.  
  
## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms  
 La première étape consiste à créer un **Application Windows Forms**.  
  
#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows  
  
1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .  
  
2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.  

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.  

4. Nommez le projet **TableAdapterDbDirectMethodsWalkthrough**, puis choisissez **OK**. 
  
     Le **TableAdapterDbDirectMethodsWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données  
 Cette étape utilise la **Assistant de Configuration de Source de données** pour créer une source de données basée sur la `Region` table dans la base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [Comment : Install Sample Databases](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Sur le **données** menu, sélectionnez **afficher les Sources de données**.  
  
2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.  
  
3.  Sur le **choisir un Type de Source de données** écran, sélectionnez **base de données**, puis sélectionnez **suivant**.  
  
4.  Sur le **choisir votre connexion de données** , effectuez une des valeurs suivantes :  
  
    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.  
  
         ou  
  
    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis sélectionnez **suivant**.  
  
6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** écran, sélectionnez **suivant**.  
  
7.  Sur le **choisir vos objets de base de données** écran, développez le **Tables** nœud.  
  
8.  Sélectionnez le `Region` de table, puis sélectionnez **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le `Region` table apparaît dans le **des Sources de données** fenêtre.  
  
## <a name="add-controls-to-the-form-to-display-the-data"></a>Ajouter des contrôles au formulaire pour afficher les données  
 Créer des contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre vers votre formulaire.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Pour créer des données liées à des contrôles sur le formulaire Windows  
  
-   Faites glisser le **région** nœud à partir de la **des Sources de données** fenêtre sur le formulaire.  
  
     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Pour ajouter des boutons pour appeler les méthodes DbDirect individuelles de TableAdapter  
  
1.  Faites glisser trois <xref:System.Windows.Forms.Button> des contrôles de la **boîte à outils** sur **Form1** (sous la **RegionDataGridView**).  
  
2.  Définissez les éléments suivants **nom** et **texte** propriétés sur chaque bouton.  
  
    |Nom|Texte|  
    |----------|----------|  
    |`InsertButton`|**INSERT**|  
    |`UpdateButton`|**Mettre à jour**|  
    |`DeleteButton`|**Supprimer**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Pour ajouter du code afin d'insérer de nouveaux enregistrements dans la base de données  
  
1.  Sélectionnez **InsertButton** pour créer un gestionnaire d’événements pour l’événement click et ouvrir votre formulaire dans l’éditeur de code.  
  
2.  Remplacez le gestionnaire d'événements `InsertButton_Click` par le code suivant :  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Pour ajouter du code afin de mettre à jour des enregistrements dans la base de données  
  
1.  Double-cliquez sur le **UpdateButton** pour créer un gestionnaire d’événements pour l’événement click et ouvrir votre formulaire dans l’éditeur de code.  
  
2.  Remplacez le gestionnaire d'événements `UpdateButton_Click` par le code suivant :  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Pour ajouter du code pour supprimer les enregistrements de la base de données  
  
1.  Sélectionnez **DeleteButton** pour créer un gestionnaire d’événements pour l’événement click et ouvrir votre formulaire dans l’éditeur de code.  
  
2.  Remplacez le gestionnaire d'événements `DeleteButton_Click` par le code suivant :  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## <a name="run-the-application"></a>Exécuter l'application  
  
#### <a name="to-run-the-application"></a>Pour exécuter l’application  
  
-   Sélectionnez **F5** pour exécuter l’application.  
  
-   Sélectionnez le **insérer** bouton et vérifiez que le nouvel enregistrement apparaît dans la grille.  
  
-   Sélectionnez le **mise à jour** bouton, puis vérifiez que l’enregistrement est mis à jour dans la grille.  
  
-   Sélectionnez le **supprimer** bouton, puis vérifiez que l’enregistrement est supprimé de la grille.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, il existe plusieurs étapes, que vous souhaiterez peut-être effectuer après la création d’un formulaire lié aux données. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout d'une fonctionnalité de recherche au formulaire.  
  
-   Ajout de tables supplémentaires au groupe de données en sélectionnant **configurer le DataSet avec l’Assistant** depuis le **des Sources de données** fenêtre. Vous pouvez ajouter des contrôles pour afficher les données associées en faisant glisser les nœuds associés vers le formulaire. Pour plus d’informations, consultez [des relations dans les jeux de données](relationships-in-datasets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)