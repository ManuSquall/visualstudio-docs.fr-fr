---
title: Créer un formulaire Windows pour rechercher des données | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], paramaterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a64377e2689ca4e5111f316c13808aee6cfb59be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505591"
---
# <a name="create-a-windows-form-to-search-data"></a>Créer un Windows Form pour rechercher des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [créer un formulaire Windows pour rechercher des données](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-form-to-search-data).  
  
  
Un scénario d'application courant consiste à afficher les données sélectionnées dans un formulaire. Par exemple, supposons que vous souhaitiez afficher les commandes d'un client spécifique ou les détails d'une commande spécifique. Dans ce scénario, un utilisateur entre des informations dans un formulaire, puis une requête est exécutée prenant l'entrée de l'utilisateur comme paramètre. C'est-à-dire que les données sont sélectionnées selon une requête paramétrable. La requête retourne uniquement les données répondant aux critères entrés par l'utilisateur. Cette procédure pas à pas indique comment créer une requête retournant les clients d'une ville spécifique et modifier l'interface utilisateur de sorte que les utilisateurs puissent entrer un nom de ville et appuyer sur un bouton pour exécuter la requête.  
  
 L'utilisation des requêtes paramétrables renforce l'efficacité de votre application en utilisant la base de données de la meilleure manière possible : pour filtrer rapidement des enregistrements. En revanche, si vous demandez une table de base de données entière, transférez sur le réseau et ensuite utilisez logique d’application pour rechercher les enregistrements souhaités, votre application peut devenir lente et inefficace.  
  
 Vous pouvez ajouter des requêtes paramétrables à n’importe quel TableAdapter (et contrôles pour accepter les valeurs de paramètre et exécuter la requête), à l’aide de la **Générateur de critères de recherche** boîte de dialogue. Ouvrez la boîte de dialogue en sélectionnant le **ajouter une requête** commande sur le **données** menu (ou sur toute balise active TableAdapter).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un nouveau projet d’Application de Windows Forms.  
  
-   Création et configuration de la source de données dans votre application avec le **Configuration de Source de données** Assistant.  
  
-   Définissant le type de déplacement des éléments dans le **des Sources de données**fenêtre.  
  
-   Création de contrôles qui affichent des données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers un formulaire.  
  
-   Ajout de contrôles pour afficher les données dans le formulaire.  
  
-   Fin de la **Générateur de critères de recherche** boîte de dialogue.  
  
-   Entrée de paramètres dans le formulaire et l’exécution de la requête paramétrable.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  
  
## <a name="create-the-windows-application"></a>Créer l’Application Windows  
 La première étape consiste à créer un **Windows Application**. Affectation d’un nom au projet est facultative à ce stade, mais vous devez lui donner un nom ici, car vous allez l’enregistrer ultérieurement.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Pour créer le projet d'application Windows  
  
1.  À partir de la **fichier** menu, créez un nouveau projet.  
  
2.  Attribuez un nom au projet `WindowsSearchForm`.  
  
3.  Sélectionnez **Windows Application** et cliquez sur **OK**.  
  
     Le **WindowsSearchForm** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="create-the-data-source"></a>Créer la source de données  
 Cette étape crée une source de données à partir d’une base de données à l’aide de la **Configuration de Source de données** Assistant. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [bases de données exemple installer SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur le formulaire. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (fonctionnalité de recherche) à la requête  
 Vous pouvez ajouter une clause WHERE à la requête d’origine en utilisant le **Générateur de critères de recherche** boîte de dialogue.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Pour créer une requête paramétrable et des contrôles pour entrer les paramètres  
  
1.  Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôler, puis choisissez **ajouter une requête** sur le **données** menu.  
  
2.  Type `FillByCity` dans le **nouveau nom de requête** zone sur le **Générateur de critères de recherche** boîte de dialogue.  
  
3.  Ajouter `WHERE City = @City` à la requête dans le **texte de la requête** zone.  
  
     La requête doit ressembler à la suivante :  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Les sources de données Access et OleDb utilisent le point d’interrogation (« ? ») pour indiquer les paramètres, par conséquent, la clause WHERE ressemblerait à ceci : `WHERE City = ?`.  
  
4.  Cliquez sur **OK** pour fermer la **Générateur de critères de recherche** boîte de dialogue.  
  
     Un **FillByCityToolStrip** est ajouté au formulaire.  
  
## <a name="testing-the-application"></a>Test de l'application  
 L'exécution de l'application ouvre votre formulaire prêt à utiliser le paramètre comme entrée.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur F5 pour exécuter l'application.  
  
2.  Type **Londres** dans le **Ville** zone de texte, puis cliquez sur **FillByCity**.  
  
     La grille de données est remplie avec les clients qui répondent aux critères. Dans cet exemple, la grille de données affiche uniquement les clients qui ont une valeur de **Londres** dans leurs **Ville** colonne.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un formulaire paramétrable. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :  
  
-   Ajout de contrôles affichant les données associées. Pour plus d’informations, consultez la page [Comment : afficher des données connexes dans une application Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Modification du dataset pour ajouter ou supprimer des objets de base de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

