---
title: Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a1393f45c46709e4085d7e170265b92c6e00266
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219482"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Lors de l’affichage des données dans les Windows Forms, vous pouvez choisir des contrôles existants à partir de la **boîte à outils**, ou vous pouvez créer des contrôles personnalisés si votre application requiert des fonctionnalités non disponibles dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.LookupBindingPropertiesAttribute> peuvent contenir trois propriétés pouvant être liées aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.ComboBox>.  
  
 Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du Design](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Lors de la création de contrôles à utiliser dans les scénarios de liaison de données, vous devez implémenter l’un des attributs de liaison de données suivants :  
  
|Utilisation d’attributs de liaison de données|  
|-----------------------------------|  
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implémentez <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. (Ce processus est décrit dans cette page de procédure pas à pas.)|  
  
 Cette procédure pas à pas crée un contrôle de recherche qui effectue une liaison vers les données de deux tables. Cet exemple utilise les tables `Customers` et `Orders` de l'exemple de base de données Northwind. Le contrôle de recherche sera lié au champ `CustomerID` de la table `Orders`. Il utilisera cette valeur pour rechercher le `CompanyName` dans la table `Customers`.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Créer un nouveau **Windows Application**.  
  
-   Ajouter un nouveau **contrôle utilisateur** à votre projet.  
  
-   Concevoir visuellement le contrôle utilisateur.  
  
-   Implémenter l'attribut `LookupBindingProperty`.  
  
-   Créer un jeu de données avec le **Configuration de Source de données** Assistant.  
  
-   Définir le **CustomerID** colonne sur le **commandes** de table, dans le **des Sources de données** fenêtre, à utiliser le nouveau contrôle.  
  
-   Créer un formulaire pour afficher des données dans le nouveau contrôle.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind.  
  
## <a name="create-a-windows-application"></a>Créer une Application Windows  
 La première étape consiste à créer un **Windows Application**.  
  
#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows  
  
1.  Dans Visual Studio, à partir de la **fichier** menu, créez un **projet**.  
  
2.  Nommez le projet **LookupControlWalkthrough**.  
  
3.  Sélectionnez **Windows Forms Application**, puis cliquez sur **OK**.  
  
     Le **LookupControlWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet  
 Cette procédure pas à pas crée un contrôle de recherche à partir d’un **contrôle utilisateur**, donc ajouter un **contrôle utilisateur** d’élément à la **LookupControlWalkthrough** projet.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Pour ajouter un contrôle utilisateur au projet  
  
1.  À partir de la **projet** menu, sélectionnez **ajouter un contrôle utilisateur**.  
  
2.  Type `LookupBox` dans le **nom** zone, puis cliquez sur **ajouter**.  
  
     Le **LookupBox** contrôle est ajouté à **l’Explorateur de solutions**et s’ouvre dans le concepteur.  
  
## <a name="design-the-lookupbox-control"></a>Concevoir le contrôle LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Pour concevoir le contrôle LookupBox  
  
-   Faites glisser un <xref:System.Windows.Forms.ComboBox> à partir de la **boîte à outils** aire de conception du contrôle utilisateur.  
  
## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut de liaison de données requis  
 Pour des contrôles de recherche prenant en charge la liaison de données, vous pouvez implémenter l’attribut<xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Pour implémenter l'attribut LookupBindingProperties  
  
1.  Commutateur le **LookupBox** contrôle en mode code. (Sur le **vue** menu, choisissez **Code**.)  
  
2.  Remplacez le code de `LookupBox` par le code suivant :  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données  
 Cette étape crée une source de données à l’aide de la **Configuration de Source de données** Assistant, selon le `Customers` et `Orders` tables dans la base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [bases de données exemple installer SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Sélectionnez le `Customers` et `Orders` tables, puis cliquez sur **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le `Customers` et `Orders` tables apparaissent dans le **des Sources de données** fenêtre.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Définir la colonne CustomerID de la table Orders pour utiliser le contrôle LookupBox  
 Dans le **des Sources de données** fenêtre, vous pouvez définir le contrôle à créer avant de faire glisser des éléments sur votre formulaire.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Pour définir la colonne CustomerID pour qu'elle soit liée au contrôle LookupBox  
  
1.  Ouvrez **Form1** dans le concepteur.  
  
2.  Développez le **clients** nœud dans le **des Sources de données** fenêtre.  
  
3.  Développez le **commandes** nœud (celui de la **clients** nœud ci-dessous le **télécopie** colonne).  
  
4.  Cliquez sur la flèche déroulante la **commandes** nœud, puis choisissez **détails** à partir de la liste de contrôle.  
  
5.  Cliquez sur la flèche déroulante la **CustomerID** colonne (dans le **commandes** nœud), puis choisissez **personnaliser**.  
  
6.  Sélectionnez le **LookupBox** dans la liste des **contrôles associés** dans le **Options de personnalisation de l’interface utilisateur de données** boîte de dialogue.  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez sur la flèche déroulante du **CustomerID** colonne, puis choisissez **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols au formulaire  
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre sur **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Pour créer des contrôles liés aux données dans le formulaire Windows  
  
-   Faites glisser le **commandes** nœud à partir de la **Sources de données** fenêtre vers le formulaire Windows et vérifiez que le **LookupBox** contrôle est utilisé pour afficher les données dans le `CustomerID` colonne.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Lier le contrôle pour rechercher CompanyName à partir de la table Customers  
  
#### <a name="to-setup-the-lookup-bindings"></a>Pour configurer les liaisons de recherche  
  
-   Sélectionnez la principale **clients** nœud dans le **des Sources de données** et faire glisser vers la liste déroulante zone dans le **CustomerIDLookupBox** sur **Form1** .  
  
     Cela configure la liaison de données pour afficher le `CompanyName` à partir de la `Customers` table, tout en conservant la `CustomerID` valeur à partir de la `Orders` table.  
  
## <a name="running-the-application"></a>Exécution de l’application  
  
#### <a name="to-run-the-application"></a>Pour exécuter l’application  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
-   Parcourez quelques enregistrements et vérifiez que le `CompanyName` s’affiche dans le `LookupBox` contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

