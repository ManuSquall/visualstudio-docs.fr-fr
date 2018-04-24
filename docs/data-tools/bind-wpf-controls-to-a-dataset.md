---
title: Lier des contrôles WPF à un dataset
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2f3085be670a3344bc8239de5e4dfe4c8f11303
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Lier des contrôles WPF à un dataset
Dans cette procédure pas à pas, vous allez créer une application WPF qui contient des contrôles liés aux données. Les contrôles sont liés aux enregistrements produit encapsulés dans un dataset. Vous allez également ajouter des boutons pour parcourir les produits et enregistrer les modifications apportées aux enregistrements produit.

Cette procédure pas à pas décrit les tâches suivantes :

- création d'une application WPF et d'un dataset généré à partir des données de l'exemple de base de données AdventureWorksLT ;

- Création d’un ensemble de contrôles liés aux données en faisant glisser une table de données à partir de la **des Sources de données** fenêtre à une fenêtre dans le Concepteur WPF.

- création de boutons permettant d'avancer et de reculer dans les enregistrements produit ;

- création d'un bouton permettant d'enregistrer les modifications effectuées par les utilisateurs sur les enregistrements produit dans la table de données et la source de données sous-jacente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis
Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT. Vous pouvez télécharger la base de données AdventureWorksLT à partir de la [site CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).

La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :

-   Datasets et TableAdapters. Pour plus d’informations, consultez [outils Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) et [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

-   Liaison de données WPF. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Créer le projet
 Créez un projet WPF. Le projet affichera les enregistrements produit.

#### <a name="to-create-the-project"></a>Pour créer le projet

1.  Démarrez Visual Studio.

2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3.  Développez **Visual Basic** ou **Visual C#**, puis sélectionnez **Windows**.

4.  Sélectionnez le **Application WPF** modèle de projet.

5.  Dans le **nom** , tapez `AdventureWorksProductsEditor` et cliquez sur **OK**.

     Visual Studio crée le `AdventureWorksProductsEditor` projet.

## <a name="create-a-dataset-for-the-application"></a>Créer un jeu de données pour l’application
 Avant de pouvoir créer des contrôles liés aux données, vous devez définir un modèle de données pour votre application et l’ajouter à la **des Sources de données** fenêtre. Dans cette procédure pas à pas, vous allez créer un dataset à utiliser comme modèle de données.

#### <a name="to-create-a-dataset"></a>Pour créer un dataset

1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

     Le **des Sources de données** fenêtre s’ouvre.

2.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

     Le **Configuration de Source de données** Assistant s’ouvre.

3.  Sur le **choisir un Type de Source de données** page, sélectionnez **base de données**, puis cliquez sur **suivant**.

4.  Sur le **choisir un modèle de base de données** page, sélectionnez **Dataset**, puis cliquez sur **suivant**.

5.  Sur le **choisir votre connexion de données** page, sélectionnez une des options suivantes :

    -   Si une connexion de données à la base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la, puis **suivant**.

    -   Cliquez sur **nouvelle connexion**et créer une connexion à la base de données AdventureWorksLT.

6.  Sur le **enregistrer la chaîne de connexion dans le fichier de configuration** page, sélectionnez le **Oui, enregistrer la connexion en tant que** case à cocher, puis cliquez sur **suivant**.

7.  Sur le **choisir vos objets de base de données** page, développez **Tables**, puis sélectionnez le **Product (SalesLT)** table.

8.  Cliquez sur **Terminer**.

     Visual Studio ajoute un nouveau `AdventureWorksLTDataSet.xsd` fichier pour le projet et il ajoute un correspondant **AdventureWorksLTDataSet** d’élément à la **des Sources de données** fenêtre. Le `AdventureWorksLTDataSet.xsd` fichier définit un dataset typé nommé `AdventureWorksLTDataSet` et un TableAdapter nommé `ProductTableAdapter`. Plus loin dans cette procédure pas à pas, vous allez utiliser le `ProductTableAdapter` pour remplir le dataset avec des données et enregistrer les modifications dans la base de données.

9. Générez le projet.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modifier la méthode de remplissage par défaut du TableAdapter
 Pour remplir le dataset avec des données, utilisez la méthode `Fill` du `ProductTableAdapter`. Par défaut, la méthode `Fill` remplit le `ProductDataTable` du `AdventureWorksLTDataSet` avec toutes les lignes de données de la table Product. Vous pouvez modifier cette méthode pour qu'elle ne retourne qu'un sous-ensemble des lignes. Pour cette procédure pas à pas, modifiez la méthode `Fill` pour ne retourner que les lignes des produits qui disposent de photos.

#### <a name="to-load-product-rows-that-have-photos"></a>Pour charger les lignes des produits disposant de photos

1.  Dans **l’Explorateur de solutions**, double-cliquez sur le `AdventureWorksLTDataSet.xsd` fichier.

     Le Concepteur de DataSet s'ouvre.

2.  Dans le concepteur, cliquez sur le **Fill, GetData** de requête et sélectionnez **configurer**.

     Le **Configuration de TableAdapter** Assistant s’ouvre.

3.  Dans le **Entrez une instruction SQL** , ajoutez la clause WHERE suivante après la `SELECT` instruction dans la zone de texte.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  Cliquez sur **Terminer**.

## <a name="define-the-user-interface"></a>Définir l’interface utilisateur
 Ajoutez plusieurs boutons à la fenêtre en modifiant le code XAML dans le Concepteur WPF. Plus loin dans cette procédure pas à pas, vous allez ajouter du code permettant aux utilisateurs de parcourir les produits et d'enregistrer les modifications apportées à ces derniers à l'aide de ces boutons.

#### <a name="to-define-the-user-interface-of-the-window"></a>Pour définir l'interface utilisateur de la fenêtre

1.  Dans **l’Explorateur de solutions**, double-cliquez sur MainWindow.xaml.

     La fenêtre s'ouvre dans le Concepteur WPF.

2.  Dans la vue [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] du concepteur, ajoutez le code suivant entre les balises `<Grid>` :

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Générez le projet.

## <a name="create-data-bound-controls"></a>Créer des contrôles liés aux données
 Créer des contrôles qui affichent les enregistrements client en faisant glisser le `Product` de table à partir de la **des Sources de données** fenêtre vers le Concepteur WPF.

#### <a name="to-create-data-bound-controls"></a>Pour créer des contrôles liés aux données

1.  Dans le **des Sources de données** fenêtre, cliquez sur le menu déroulant pour le **produit** nœud et sélectionnez **détails**.

2.  Développez le **produit** nœud.

3.  Pour cet exemple, certains champs n’apparaissent pas, par conséquent, cliquez sur le menu déroulant en regard des nœuds suivants et sélectionnez **aucun**:

    -   ProductCategoryID

    -   ProductModelID

    -   ThumbnailPhotoFileName

    -   rowguid

    -   ModifiedDate

4.  Cliquez sur le menu déroulant en regard du **ThumbNailPhoto** nœud et sélectionnez **Image**.

    > [!NOTE]
    >  Par défaut, les éléments de la **des Sources de données** fenêtre qui représentent des images ont leur contrôle par défaut la valeur **aucun**. En effet, les images sont stockées en tant que tableaux d'octets dans les bases de données et les tableaux d'octets peuvent contenir aussi bien un simple tableau d'octets que le fichier exécutable d'une application volumineuse.

5.  À partir de la **des Sources de données** fenêtre, faites glisser le **produit** nœud à la ligne de la grille sous la ligne qui contient les boutons.

     Visual Studio génère du code XAML qui définit un ensemble de contrôles liés aux données dans le **produits** table. Il génère également du code qui charge les données. Pour plus d’informations sur le XAML et le code généré, consultez [WPF de lier des contrôles aux données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6.  Dans le concepteur, cliquez sur la zone de texte en regard du **ID de produit** étiquette.

7.  Dans le **propriétés** fenêtre, sélectionnez la case à cocher à côté du **IsReadOnly** propriété.

## <a name="navigating-product-records"></a>Parcourir les enregistrements de produit
 Ajoutez le code qui permet aux utilisateurs de faire défiler les enregistrements produit à l’aide de la **\<** et **>** boutons.

#### <a name="to-enable-users-to-navigate-product-records"></a>Pour permettre aux utilisateurs de parcourir les enregistrements produit

1.  Dans le concepteur, double-cliquez sur le **<** bouton sur la surface de la fenêtre.

     Visual Studio ouvre le fichier code-behind et crée un nouveau `backButton_Click` Gestionnaire d’événements pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.

2.  Modifier la `Window_Loaded` Gestionnaire d’événements, donc la `ProductViewSource`, `AdventureWorksLTDataSet`, et `AdventureWorksLTDataSetProductTableAdapter` sont en dehors de la méthode et accessibles par tout le formulaire. Déclarer uniquement ces global au formulaire et les assigner au sein de la `Window_Loaded` Gestionnaire d’événements semblable au suivant :

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3.  Ajoutez le code suivant au gestionnaire d'événements `backButton_Click` :

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4.  Retourner au concepteur et double-cliquez sur le **>** bouton.

5.  Ajoutez le code suivant au gestionnaire d'événements `nextButton_Click` :

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Enregistrer les modifications apportées aux enregistrements produit
Ajoutez le code qui permet aux utilisateurs d’enregistrer les modifications apportées aux enregistrements produit à l’aide de la **enregistrer les modifications** bouton.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Pour ajouter la possibilité d'enregistrer les modifications apportées aux enregistrements produit

1.  Dans le concepteur, double-cliquez sur le **enregistrer les modifications** bouton.

     Visual Studio ouvre le fichier code-behind et crée un nouveau `saveButton_Click` Gestionnaire d’événements pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.

2.  Ajoutez le code suivant au gestionnaire d'événements `saveButton_Click` :

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    >  Cet exemple utilise la méthode `Save` de `TableAdapter` pour enregistrer les modifications. Cela nous convient dans cette procédure pas à pas, car une seule table de données est modifiée. Si vous devez enregistrer des modifications dans plusieurs tables de données, utilisez plutôt la méthode `UpdateAll` de `TableAdapterManager` générée par Visual Studio avec votre dataset. Pour plus d’informations, consultez [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Tester l’application
 Générez et exécutez l’application. Vérifiez que vous pouvez afficher et mettre à jour les enregistrements produit.

#### <a name="to-test-the-application"></a>Pour tester l'application

1.  Appuyez sur **F5**.

     L'application se génère et s'exécute. Vérifiez ce qui suit :

    -   Les zones de texte affichent les données du premier enregistrement produit qui dispose d'une photo. Ce produit a l’ID de produit 713 et le nom **Long-Sleeve Logo Jersey, S**.

    -   Vous pouvez cliquer sur le **>** ou **<** boutons pour parcourir les autres enregistrements produit.

2.  Dans un des enregistrements de produit, modifiez le **taille** valeur, puis cliquez sur **enregistrer les modifications**.

3.  Fermez l’application et redémarrez l’application en appuyant sur **F5** dans Visual Studio.

4.  Accédez à l'enregistrement produit que vous avez modifié et vérifiez que la modification a été appliquée.

5.  Fermez l'application.

## <a name="next-steps"></a>Étapes suivantes
 Une fois cette procédure pas à pas terminée, vous pouvez effectuer les tâches associées suivantes :

-   Découvrez comment utiliser le **des Sources de données** contrôle de fenêtre dans Visual Studio pour lier WPF à d’autres types de sources de données. Pour plus d’informations, consultez [WPF de lier des contrôles à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

-   Découvrez comment utiliser le **des Sources de données** fenêtre dans Visual Studio pour afficher les données associées (autrement dit, les données dans une relation parent-enfant) dans des contrôles WPF. Pour plus d’informations, consultez [procédure pas à pas : affichage des données connexes dans une Application WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Vue d’ensemble de la liaison de données](/dotnet/framework/wpf/data/data-binding-overview)