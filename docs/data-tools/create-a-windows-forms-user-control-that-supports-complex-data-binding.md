---
title: Créer un contrôle utilisateur Windows Forms avec liaison de données | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f7dac1b763e444349f741f72dae8c41fa8087a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe

Lors de l’affichage des données sur les formulaires dans les applications Windows, vous pouvez choisir des contrôles existants à partir de la **boîte à outils**, ou vous pouvez créer des contrôles personnalisés si votre application nécessite des fonctionnalités qui ne sont pas disponible dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contiennent une propriété `DataSource` et `DataMember` pouvant être liée aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.

Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Lors de la création de contrôles à utiliser dans les scénarios de liaison de données, vous devez implémenter l’un des attributs de liaison de données suivants :

|Utilisation d’attributs de liaison de données|
|-----------------------------------|
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. (Ce processus est décrit dans cette page de procédure pas à pas.)|
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Cette procédure pas à pas crée un contrôle complexe affichant les lignes de données d'une table. Cet exemple utilise la table `Customers` de l'exemple de base de données Northwind. Le contrôle utilisateur complexe affiche la table de clients dans un <xref:System.Windows.Forms.DataGridView> dans le contrôle personnalisé.

Pendant cette procédure pas à pas, vous allez apprendre à :

- Créer un nouveau **Application Windows Forms**.

- Ajouter un nouveau **contrôle utilisateur** à votre projet.

- Concevoir visuellement le contrôle utilisateur.

- Implémenter l'attribut `ComplexBindingProperty`.

- Créer un dataset avec le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png).

- Définir le **clients** de table dans le [fenêtre Sources de données](add-new-data-sources.md) à utiliser le nouveau contrôle complexe.

- Ajoutez le nouveau contrôle en le faisant glisser à partir de la **fenêtre Sources de données** sur **Form1**.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le programme d’installation Visual Studio, SQL Server Express LocalDB peut être installé dans le cadre de la **stockage de données et de traitement** charge de travail, ou sous la forme d’un composant individuel.

1. Installer la base de données Northwind en procédant comme suit :

    1. Dans Visual Studio, ouvrez le **l’Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête...** .

       Une fenêtre d’éditeur de requête s’ouvre.

    1. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans le Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    1. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée et la base de données Northwind est créé.

## <a name="create-a-windows-forms-application"></a>Créer une application Windows Forms

 La première étape consiste à créer un **Application Windows Forms**.

### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau**, **projet...** .

1. Développez le **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **de bureau Windows classique**.

1. Dans le volet central, sélectionnez le **l’application Windows Forms** type de projet.

1. Nommez le projet **ComplexControlWalkthrough**, puis choisissez **OK**.

    Le **ComplexControlWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet

Étant donné que cette procédure pas à pas crée un contrôle complexe pouvant être lié aux données d’une **contrôle utilisateur**, vous devez ajouter un **contrôle utilisateur** élément au projet.

### <a name="to-add-a-user-control-to-the-project"></a>Pour ajouter un contrôle utilisateur au projet

1. À partir de la **projet** menu, choisissez **ajouter un contrôle utilisateur**.

1. Type **ComplexDataGridView** dans les **nom** zone, puis cliquez sur **ajouter**.

    Le **ComplexDataGridView** contrôle est ajouté à **l’Explorateur de solutions**et s’ouvre dans le concepteur.

## <a name="design-the-complexdatagridview-control"></a>Concevoir le contrôle ComplexDataGridView

Cette étape ajoute un <xref:System.Windows.Forms.DataGridView> au contrôle utilisateur.

### <a name="to-design-the-complexdatagridview-control"></a>Pour concevoir le contrôle ComplexDataGridView

- Faites glisser un <xref:System.Windows.Forms.DataGridView> à partir de la **boîte à outils** sur l’aire de conception du contrôle utilisateur.

## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut DataBinding requis

Pour des contrôles complexes prenant en charge la liaison de données, vous pouvez implémenter l'attribut<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.
  
### <a name="to-implement-the-complexbindingproperties-attribute"></a>Pour implémenter l'attribut ComplexBindingProperties

1. Commutateur le **ComplexDataGridView** contrôle en mode code. (Sur le **vue** menu, sélectionnez **Code**.)

1. Remplacez le code de `ComplexDataGridView` par le code suivant :

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="creating-a-data-source-from-your-database"></a>Création d’une source de données à partir de votre base de données

Cette étape utilise la **Configuration de Source de données** l’Assistant pour créer une source de données basée sur la `Customers` table dans la base de données Northwind.

### <a name="to-create-the-data-source"></a>Pour créer la source de données

1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

2.  Dans le **des Sources de données** fenêtre, sélectionnez **ajouter une nouvelle Source de données** pour démarrer le **Configuration de Source de données** Assistant.

3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4.  Sur le **choisir votre connexion de données** page, procédez comme suit :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    - Sélectionnez **nouvelle connexion** pour lancer le **Ajouter/modifier la connexion** boîte de dialogue.

5.  Si votre base de données requiert un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **suivant**.

6.  Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

7.  Sur le **choisir vos objets de base de données** page, développez le **Tables** nœud.

8.  Sélectionnez le `Customers` de table, puis cliquez sur **Terminer**.

    Le **NorthwindDataSet** est ajouté à votre projet et le `Customers` table apparaît dans le **des Sources de données** fenêtre.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Définir la table Customers pour utiliser le contrôle ComplexDataGridView

Dans le **des Sources de données** fenêtre, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Pour définir la table Customers pour qu'elle soit liée au contrôle ComplexDataGridView

1. Ouvrez **Form1** dans le concepteur.

1. Développez le **clients** nœud dans le **des Sources de données** fenêtre.

1. Cliquez sur la flèche déroulante du **clients** nœud, puis choisissez **personnaliser**.

1. Sélectionnez le **ComplexDataGridView** dans la liste des **contrôles associés** dans les **Options de personnalisation de l’interface utilisateur de données** boîte de dialogue.

1. Cliquez sur la flèche déroulante du `Customers` de table, puis choisissez **ComplexDataGridView** à partir de la liste de contrôle.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre vers votre formulaire.

### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire

Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre sur le formulaire. Vérifiez que le **ComplexDataGridView** contrôle est utilisé pour afficher les données de la table.  

## <a name="running-the-application"></a>Exécution de l’application

### <a name="to-run-the-application"></a>Pour exécuter l’application

Appuyez sur F5 pour exécuter l'application.

## <a name="next-steps"></a>Étapes suivantes

Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un contrôle prenant en charge la liaison de données. Les étapes ultérieures sont habituellement celles-ci :

- Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.

- Création de contrôles prenant en charge les scénarios de recherche. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Voir aussi

[Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)  
[Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)  
[Contrôles Windows Forms](/dotnet/framework/winforms/controls/index)
