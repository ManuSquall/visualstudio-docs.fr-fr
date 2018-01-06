---
title: "Créer un Windows Form pour rechercher des données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: fd882c536fefde9a9eb6ab546d6049d1f1216771
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-windows-form-to-search-data"></a>Créer un Windows Form pour rechercher des données
Un scénario d'application courant consiste à afficher les données sélectionnées dans un formulaire. Par exemple, supposons que vous souhaitiez afficher les commandes d'un client spécifique ou les détails d'une commande spécifique. Dans ce scénario, un utilisateur entre des informations dans un formulaire, puis une requête est exécutée prenant l'entrée de l'utilisateur comme paramètre. C'est-à-dire que les données sont sélectionnées selon une requête paramétrable. La requête retourne uniquement les données répondant aux critères entrés par l'utilisateur. Cette procédure pas à pas indique comment créer une requête retournant les clients d'une ville spécifique et modifier l'interface utilisateur de sorte que les utilisateurs puissent entrer un nom de ville et appuyer sur un bouton pour exécuter la requête.  
  
 L'utilisation des requêtes paramétrables renforce l'efficacité de votre application en utilisant la base de données de la meilleure manière possible : pour filtrer rapidement des enregistrements. En revanche, si vous demandez une table de base de données entière, transférez sur le réseau, puis utilisez la logique d’application pour rechercher les enregistrements souhaités, votre application peut devenir lente et inefficace.  
  
 Vous pouvez ajouter des requêtes paramétrables à n’importe quel TableAdapter (et des contrôles pour accepter des valeurs de paramètre et exécuter la requête), à l’aide de la **Générateur de critères de recherche** boîte de dialogue. Ouvrez la boîte de dialogue en sélectionnant le **ajouter une requête** commande sur le **données** menu (ou sur toute balise active TableAdapter).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Application Windows Forms.  
  
-   Création et configuration de la source de données dans votre application avec le **Configuration de Source de données** Assistant.  
  
-   Définir le type de déplacement des éléments dans le **des Sources de données**fenêtre.  
  
-   Création de contrôles qui affichent des données en faisant glisser des éléments depuis la **des Sources de données** fenêtre dans un formulaire.  
  
-   Ajout de contrôles pour afficher les données dans le formulaire.  
  
-   Fin de la **Générateur de critères de recherche** boîte de dialogue.  
  
-   Entrée de paramètres dans le formulaire et l’exécution de la requête paramétrable.  
  
## <a name="prerequisites"></a>Prérequis  
Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.  
  
1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement des éditions de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.  
  
2.  Installer la base de données Northwind en procédant comme suit :  

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .  

       Une fenêtre d’éditeur de requête s’ouvre.  

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.  

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.  

       Après une courte période, la requête est terminée et la base de données Northwind est créé.  
  
## <a name="create-the-windows-forms-application"></a>Créer l’Application Windows Forms  
 La première étape consiste à créer un **Application Windows Forms**. Attribution d’un nom au projet est facultative à ce stade, mais vous devez lui donner un nom ici, car vous allez enregistrer le projet ultérieurement.  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>Pour créer le nouveau projet d’Application Windows Forms  
  
1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .  
  
2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.  

3. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.  

4. Nommez le projet **WindowsSearchForm**, puis choisissez **OK**. 
  
     Le **WindowsSearchForm** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="create-the-data-source"></a>Créer la source de données  
Cette étape crée une source de données à partir d’une base de données à l’aide de la **Configuration de Source de données** Assistant.  
  
#### <a name="to-create-the-data-source"></a>Pour créer la source de données  
  
1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Configuration de Source de données** Assistant.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.  
  
4.  Sur le **choisir votre connexion de données** page, procédez comme suit :  
  
    -   Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.  
  
    -   Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue.  
  
5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **suivant**.  
  
6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.  
  
7.  Sur le **choisir vos objets de base de données** page, développez le **Tables** nœud.  
  
8.  Sélectionnez le **clients** de table, puis cliquez sur **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le **clients** table apparaît dans le **des Sources de données** fenêtre.  
  
## <a name="create-the-form"></a>Création d’un formulaire  
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre vers votre formulaire.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire  
  
1.  Développez le **clients** nœud dans le **des Sources de données** fenêtre.  
  
2.  Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre à votre formulaire.  
  
     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur le formulaire. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
## <a name="add-parameterization-search-functionality-to-the-query"></a>Ajouter le paramétrage (fonctionnalité de recherche) à la requête  
 Vous pouvez ajouter une clause WHERE à la requête d’origine à l’aide du **Générateur de critères de recherche** boîte de dialogue.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Pour créer une requête paramétrable et des contrôles pour entrer les paramètres  
  
1.  Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôler, puis choisissez **ajouter une requête** sur la **données** menu.  
  
2.  Type `FillByCity` dans les **nouveau nom de requête** zone sur le **Générateur de critères de recherche** boîte de dialogue.  
  
3.  Ajouter `WHERE City = @City` à la requête dans le **texte de la requête** zone.  
  
     La requête doit ressembler à la suivante :  
  
     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,  
          Address, City, Region, PostalCode, Country, Phone, Fax  
     FROM Customers
     WHERE City = @City  
     ```
  
    > [!NOTE]
    >  Les sources de données Access et OleDb utilisent le point d’interrogation (« ? ») pour indiquer les paramètres, par conséquent, la clause WHERE ressemblerait à ceci : `WHERE City = ?`.  
  
4.  Cliquez sur **OK** pour fermer la **Générateur de critères de recherche** boîte de dialogue.  
  
     A **FillByCityToolStrip** est ajouté au formulaire.  
  
## <a name="testing-the-application"></a>Test de l'application  
 L'exécution de l'application ouvre votre formulaire prêt à utiliser le paramètre comme entrée.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Type **Londres** dans les **Ville** zone de texte, puis cliquez sur **FillByCity**.  
  
     La grille de données est remplie avec les clients qui répondent aux critères. Dans cet exemple, la grille de données affiche uniquement les clients qui ont une valeur de **Londres** dans leurs **Ville** colonne.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un formulaire paramétrable. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout de contrôles affichant les données associées. Pour plus d’informations, consultez [des relations dans les jeux de données](relationships-in-datasets.md).  
  
-   Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)