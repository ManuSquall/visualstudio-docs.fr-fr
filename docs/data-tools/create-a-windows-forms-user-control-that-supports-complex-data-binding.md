---
title: Créer un contrôle utilisateur Windows Forms avec liaison de données
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e9f80f55aa3059cbe5c9af3b5510915f768ea20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567635"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexes

Lors de l’affichage des données dans des formulaires dans les applications Windows, vous pouvez choisir des contrôles existants à partir de la **boîte à outils**. Ou bien, vous pouvez créer des contrôles personnalisés si votre application nécessite une fonctionnalité qui n’est pas disponible dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contiennent une propriété `DataSource` et `DataMember` pouvant être liée aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.

Pour plus d’informations sur la création de contrôles, consultez [développement de formulaires Windows contrôle au moment du design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quand vous créez des contrôles utilisables dans des scénarios de liaison de données, vous devez implémenter l’un des attributs de liaison de données suivants :

|Utilisation d’attributs de liaison de données|
| - |
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. (Ce processus est décrit dans cette page de procédure pas à pas.)|
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Cette procédure pas à pas crée un contrôle complexe affichant les lignes de données d'une table. Cet exemple utilise la table `Customers` de l'exemple de base de données Northwind. Le contrôle utilisateur complexe affiche la table de clients dans un <xref:System.Windows.Forms.DataGridView> dans le contrôle personnalisé.

Au cours de cette procédure pas à pas, vous allez découvrir comment :

- Ajouter un nouveau **Contrôle utilisateur** à votre projet.

- Concevoir visuellement le contrôle utilisateur.

- Implémenter l'attribut `ComplexBindingProperty`.

- Créer un jeu de données avec le [Assistant de Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png).

- Définir le **clients** table dans le [fenêtre Sources de données](add-new-data-sources.md#data-sources-window) à utiliser le nouveau contrôle complexe.

- Ajouter le nouveau contrôle en le faisant glisser depuis la fenêtre **Sources de données** vers **Form1**.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas utilise SQL Server Express LocalDB et la base de données Northwind.

1. Si vous n’avez pas SQL Server Express LocalDB, installez-le à partir de la [page de téléchargement de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou via le **le programme d’installation de Visual Studio**. Dans le **le programme d’installation de Visual Studio**, vous pouvez installer SQL Server Express LocalDB dans le cadre de la **stockage de données et de traitement** charge de travail, ou comme un composant individuel.

1. Installer la base de données Northwind en suivant ces étapes :

    1. Dans Visual Studio, ouvrez le **Explorateur d’objets SQL Server** fenêtre. (Explorateur d’objets SQL Server est installé dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer.) Développez le **SQL Server** nœud. Avec le bouton droit sur votre instance de base de données locale et sélectionnez **nouvelle requête**.

       Une fenêtre d’éditeur de requête s’ouvre.

    1. Copie le [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) dans votre Presse-papiers. Ce script T-SQL crée la base de données Northwind à partir de zéro et la remplit avec des données.

    1. Collez le script T-SQL dans l’éditeur de requête, puis choisissez le **Execute** bouton.

       Après une courte période, la requête est terminée en cours d’exécution et la base de données Northwind est créé.

## <a name="create-a-windows-forms-app-project"></a>Créer un projet d’application Windows Forms

La première étape consiste à créer un **Windows Forms application** projet pour soit C# ou Visual Basic. Attribuez le nom **ComplexControlWalkthrough** au projet.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet

Étant donné que cette procédure pas à pas crée un contrôle complexe pouvant être lié à des données à partir d’un **contrôle utilisateur**, ajoutez un **contrôle utilisateur** élément au projet :

1. Dans le menu **Projet**, choisissez **Ajouter un contrôle utilisateur**.

1. Tapez **ComplexDataGridView** dans la zone **Nom**, puis cliquez sur **Ajouter**.

    Le contrôle **ComplexDataGridView** est ajouté à l’**Explorateur de solutions** et s’ouvre dans le concepteur.

## <a name="design-the-complexdatagridview-control"></a>Concevoir le contrôle ComplexDataGridView

Pour ajouter un <xref:System.Windows.Forms.DataGridView> au contrôle utilisateur, faites glisser un <xref:System.Windows.Forms.DataGridView> à partir de la **boîte à outils** aire de conception du contrôle utilisateur.

## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut de liaison de données requis

Pour des contrôles complexes prenant en charge la liaison de données, vous pouvez implémenter l’attribut<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> :

1. Basculez le contrôle **ComplexDataGridView** en mode Code. (Dans le menu **Affichage**, choisissez **Code**.)

1. Remplacez le code de `ComplexDataGridView` par le code suivant :

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données

Utilisez le **Configuration de Source de données** Assistant pour créer une source de données selon le `Customers` table dans la base de données Northwind :

1. Pour ouvrir le **des Sources de données** fenêtre, dans le **données** menu, cliquez sur **afficher les Sources de données**.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’Assistant **Configuration de source de données**.

3. Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.

4. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

   - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

   - Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données nécessite un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **Suivant**.

6. Sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** , cliquez sur **suivant**.

7. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

8. Sélectionnez la table `Customers`, puis cliquez sur **Terminer**.

   **NorthwindDataSet** est ajouté à votre projet et la table `Customers` apparaît dans la fenêtre **Sources de données**.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Définir la table Customers pour utiliser le contrôle ComplexDataGridView

Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire :

1. Ouvrez **Form1** dans le concepteur.

1. Développez le nœud **Customers** dans la fenêtre **Sources de données**.

1. Cliquez sur la flèche déroulante du nœud **Customers** et choisissez **Personnaliser**.

1. Sélectionnez **ComplexDataGridView** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l’interface utilisateur de données**.

1. Cliquez sur la flèche déroulante de la table `Customers` et choisissez **ComplexDataGridView** dans la liste de contrôles.

## <a name="add-controls-to-the-form"></a>Ajouter des contrôles au formulaire

Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers votre formulaire. Faites glisser le nœud **Customers** principal depuis la fenêtre **Sources de données** vers le formulaire. Vérifiez que le **ComplexDataGridView** contrôle est utilisé pour afficher les données de la table.

## <a name="run-the-application"></a>Exécuter l'application

Appuyez sur **F5** pour exécuter l’application.

## <a name="next-steps"></a>Étapes suivantes

Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un contrôle prenant en charge la liaison de données. Les étapes ultérieures sont habituellement celles-ci :

- Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.

- Création de contrôles prenant en charge les scénarios de recherche. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Contrôles Windows Forms](/dotnet/framework/winforms/controls/index)