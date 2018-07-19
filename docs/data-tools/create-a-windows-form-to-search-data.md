---
title: Créer un Windows Form pour rechercher des données
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cdc82db1f701abb26b983fe0a1f2e4c7752c6c55
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756397"
---
# <a name="create-a-windows-form-to-search-data"></a>Créer un Windows Form pour rechercher des données
Un scénario d'application courant consiste à afficher les données sélectionnées dans un formulaire. Par exemple, supposons que vous souhaitiez afficher les commandes d'un client spécifique ou les détails d'une commande spécifique. Dans ce scénario, un utilisateur entre des informations dans un formulaire, puis une requête est exécutée prenant l'entrée de l'utilisateur comme paramètre. C'est-à-dire que les données sont sélectionnées selon une requête paramétrable. La requête retourne uniquement les données répondant aux critères entrés par l'utilisateur. Cette procédure pas à pas indique comment créer une requête retournant les clients d'une ville spécifique et modifier l'interface utilisateur de sorte que les utilisateurs puissent entrer un nom de ville et appuyer sur un bouton pour exécuter la requête.

 L'utilisation des requêtes paramétrables renforce l'efficacité de votre application en utilisant la base de données de la meilleure manière possible : pour filtrer rapidement des enregistrements. En revanche, si vous demandez une table de base de données entière, transférez sur le réseau et ensuite utilisez logique d’application pour rechercher les enregistrements souhaités, votre application peut devenir lente et inefficace.

 Vous pouvez ajouter des requêtes paramétrables à n’importe quel TableAdapter (et contrôles pour accepter les valeurs de paramètre et exécuter la requête), à l’aide de la **Générateur de critères de recherche** boîte de dialogue. Ouvrez la boîte de dialogue en sélectionnant le **ajouter une requête** commande sur le **données** menu (ou sur toute balise active TableAdapter).

 Cette procédure pas à pas décrit notamment les tâches suivantes :

-   Création d’un nouveau **Windows Forms Application** projet.

-   Création et configuration de la source de données dans votre application avec le **Configuration de Source de données** Assistant.

-   Définissant le type de déplacement des éléments dans le **des Sources de données** fenêtre.

-   Création de contrôles qui affichent des données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers un formulaire.

-   Ajout de contrôles pour afficher les données dans le formulaire.

-   Fin de la **Générateur de critères de recherche** boîte de dialogue.

-   Entrée de paramètres dans le formulaire et l’exécution de la requête paramétrable.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1.  Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

2.  Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le **le programme d’installation de Visual Studio**.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    2. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    3. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-the-windows-forms-application"></a>Créer l’application Windows Forms
 La première étape consiste à créer un **Windows Forms Application**. Affectation d’un nom au projet est facultative à ce stade, mais vous devez lui donner un nom ici, car vous allez enregistrer le projet ultérieurement.

#### <a name="to-create-the-new-windows-forms-application-project"></a>Pour créer le nouveau projet d’application Windows Forms

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

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

8.  Sélectionnez le **clients** table, puis cliquez sur **Terminer**.

     Le **NorthwindDataSet** est ajouté à votre projet et le **clients** table s’affiche dans le **des Sources de données** fenêtre.

## <a name="create-the-form"></a>Création d’un formulaire
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers votre formulaire.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire

1.  Développez le **clients** nœud dans le **des Sources de données** fenêtre.

2.  Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre à votre formulaire.

     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur le formulaire. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Ajoutez le paramétrage (fonctionnalité de recherche) à la requête
 Vous pouvez ajouter une clause WHERE à la requête d’origine en utilisant le **Générateur de critères de recherche** boîte de dialogue.

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Pour créer une requête paramétrable et des contrôles pour entrer les paramètres

1.  Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôler, puis choisissez **ajouter une requête** sur le **données** menu.

2.  Type `FillByCity` dans le **nouveau nom de requête** zone sur le **Générateur de critères de recherche** boîte de dialogue.

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

     Un **FillByCityToolStrip** est ajouté au formulaire.

## <a name="testing-the-application"></a>Test de l'application
 Exécution de l’application ouvre votre formulaire et le rend prêt à utiliser le paramètre en tant qu’entrée.

#### <a name="to-test-the-application"></a>Pour tester l'application

1.  Appuyez sur **F5** pour exécuter l’application.

2.  Type **Londres** dans le **Ville** zone de texte, puis cliquez sur **FillByCity**.

     La grille de données est remplie avec les clients qui répondent aux critères. Dans cet exemple, la grille de données affiche uniquement les clients qui ont une valeur de **Londres** dans leurs **Ville** colonne.

## <a name="next-steps"></a>Étapes suivantes
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un formulaire paramétrable. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

-   Ajout de contrôles affichant les données associées. Pour plus d’informations, consultez [relations dans les Datasets](relationships-in-datasets.md).

-   Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)