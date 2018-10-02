---
title: Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe | Microsoft Docs
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27f8a0e7fca0f14ee784eddaeb30f4d734994dc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504949"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [créer un contrôle utilisateur Windows Forms avec liaison de données](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding).  
  
  
Lors de l’affichage des données dans des formulaires dans les applications Windows, vous pouvez choisir des contrôles existants à partir de la **boîte à outils**, ou vous pouvez créer des contrôles personnalisés si votre application nécessite une fonctionnalité qui n’est pas disponible dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contiennent une propriété `DataSource` et `DataMember` pouvant être liée aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.  
  
 Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du Design](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Lors de la création de contrôles à utiliser dans les scénarios de liaison de données, vous devez implémenter l’un des attributs de liaison de données suivants :  
  
|Utilisation d’attributs de liaison de données|  
|-----------------------------------|  
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. (Ce processus est décrit dans cette page de procédure pas à pas.)|  
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Cette procédure pas à pas crée un contrôle complexe affichant les lignes de données d'une table. Cet exemple utilise la table `Customers` de l'exemple de base de données Northwind. Le contrôle utilisateur complexe affiche la table de clients dans un <xref:System.Windows.Forms.DataGridView> dans le contrôle personnalisé.  
  
 Pendant cette procédure pas à pas, vous allez apprendre à :  
  
-   Créer un nouveau **Windows Application**.  
  
-   Ajouter un nouveau **contrôle utilisateur** à votre projet.  
  
-   Concevoir visuellement le contrôle utilisateur.  
  
-   Implémenter l'attribut `ComplexBindingProperty`.  
  
-   Créer un jeu de données avec le [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Définir le **clients** table dans le [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) à utiliser le nouveau contrôle complexe.  
  
-   Ajouter le nouveau contrôle en le faisant glisser à partir de la **fenêtre Sources de données** sur **Form1**.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   avoir accès à l'exemple de base de données Northwind. Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Créer une Application Windows  
 La première étape consiste à créer un **Windows Application**.  
  
#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows  
  
1.  Dans Visual Studio, à partir de la **fichier** menu, créez un **projet**.  
  
2.  Nommez le projet **ComplexControlWalkthrough**.  
  
3.  Sélectionnez **Windows Application**, puis cliquez sur **OK**. Pour plus d’informations, consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Le **ComplexControlWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.  
  
## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet  
 Étant donné que cette procédure pas à pas crée un contrôle complexe pouvant être lié à des données à partir d’un **contrôle utilisateur**, vous devez ajouter un **contrôle utilisateur** élément au projet.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Pour ajouter un contrôle utilisateur au projet  
  
1.  À partir de la **projet** menu, choisissez **ajouter un contrôle utilisateur**.  
  
2.  Type **ComplexDataGridView** dans le **nom** zone, puis cliquez sur **ajouter**.  
  
     Le **ComplexDataGridView** contrôle est ajouté à **l’Explorateur de solutions**et s’ouvre dans le concepteur.  
  
## <a name="design-the-complexdatagridview-control"></a>Concevoir le contrôle ComplexDataGridView  
 Cette étape ajoute un <xref:System.Windows.Forms.DataGridView> au contrôle utilisateur.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Pour concevoir le contrôle ComplexDataGridView  
  
-   Faites glisser un <xref:System.Windows.Forms.DataGridView> à partir de la **boîte à outils** aire de conception du contrôle utilisateur.  
  
## <a name="add-the-required-data-binding-attribute"></a>Ajoutez l’attribut de liaison de données requis  
 Pour des contrôles complexes prenant en charge la liaison de données, vous pouvez implémenter l'attribut<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Pour implémenter l'attribut ComplexBindingProperties  
  
1.  Commutateur le **ComplexDataGridView** contrôle en mode code. (Sur le **vue** menu, sélectionnez **Code**.)  
  
2.  Remplacez le code de `ComplexDataGridView` par le code suivant :  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Création d’une source de données à partir de votre base de données  
 Cette étape utilise le **Configuration de Source de données** Assistant pour créer une source de données selon le `Customers` table dans la base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion. Pour plus d’informations sur la configuration de la base de données Northwind, consultez [bases de données exemple installer SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Sélectionnez le `Customers` table, puis cliquez sur **Terminer**.  
  
     Le **NorthwindDataSet** est ajouté à votre projet et le `Customers` table s’affiche dans le **des Sources de données** fenêtre.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Définir la table Customers pour utiliser le contrôle ComplexDataGridView  
 Dans le **des Sources de données** fenêtre, vous pouvez définir le contrôle à créer avant de faire glisser des éléments sur votre formulaire.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Pour définir la table Customers pour qu'elle soit liée au contrôle ComplexDataGridView  
  
1.  Ouvrez **Form1** dans le concepteur.  
  
2.  Développez le **clients** nœud dans le **des Sources de données** fenêtre.  
  
3.  Cliquez sur la flèche déroulante du **clients** nœud, puis choisissez **personnaliser**.  
  
4.  Sélectionnez le **ComplexDataGridView** dans la liste des **contrôles associés** dans le **Options de personnalisation de l’interface utilisateur de données** boîte de dialogue.  
  
5.  Cliquez sur la flèche déroulante du `Customers` table, puis choisissez **ComplexDataGridView** à partir de la liste de contrôle.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols au formulaire  
 Vous pouvez créer les contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers votre formulaire.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire  
  
-   Faites glisser le **clients** nœud à partir de la **des Sources de données** fenêtre vers le formulaire. Vérifiez que le **ComplexDataGridView** contrôle est utilisé pour afficher les données de la table.  
  
## <a name="running-the-application"></a>Exécution de l’application  
  
#### <a name="to-run-the-application"></a>Pour exécuter l’application  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Selon les exigences de votre application, vous pouvez exécuter différentes étapes après la création d’un contrôle prenant en charge la liaison de données. Les étapes ultérieures sont habituellement celles-ci :  
  
-   Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.  
  
-   Création de contrôles prenant en charge les scénarios de recherche. Pour plus d’informations, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Contrôles Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

