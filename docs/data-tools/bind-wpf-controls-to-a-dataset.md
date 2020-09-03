---
title: Lier des contrôles WPF à un dataset
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3ad960054e0c2dfe6470c51adbd9f3675fc87952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282915"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Lier des contrôles WPF à un dataset

Dans cette procédure pas à pas, vous allez créer une application WPF qui contient des contrôles liés aux données. Les contrôles sont liés aux enregistrements produit encapsulés dans un dataset. Vous pouvez également ajouter des boutons pour parcourir les produits et enregistrer les modifications apportées aux enregistrements de produits.

Cette procédure pas à pas décrit les tâches suivantes :

- création d'une application WPF et d'un dataset généré à partir des données de l'exemple de base de données AdventureWorksLT ;

- création d’un ensemble de contrôles liés aux données en faisant glisser une table de données depuis la fenêtre **Sources de données** vers une fenêtre du Concepteur WPF ;

- création de boutons permettant d'avancer et de reculer dans les enregistrements produit ;

- création d'un bouton permettant d'enregistrer les modifications effectuées par les utilisateurs sur les enregistrements produit dans la table de données et la source de données sous-jacente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Visual Studio

- Accès à une instance en cours d’exécution de SQL Server ou SQL Server Express à laquelle l’exemple de base de données AdventureWorks Light (AdventureWorksLT) est attaché. Vous pouvez télécharger la base de données AdventureWorksLT à partir de l' [Archive CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :

- Datasets et TableAdapters. Pour plus d’informations, consultez [outils de DataSet dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) et [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- Liaison de données WPF. Pour plus d’informations, consultez [vue d’ensemble](/dotnet/desktop-wpf/data/data-binding-overview)de la liaison de données.

## <a name="create-the-project"></a>Créer le projet

Créez un projet WPF pour afficher les enregistrements de produits.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

2. Dans le menu **fichier** , sélectionnez **nouveau** > **projet**.

3. Développez **Visual Basic** ou **Visual C#**, puis sélectionnez **Windows**.

4. Sélectionnez le modèle de projet d' **application WPF** .

5. Dans la zone **nom** , entrez **AdventureWorksProductsEditor** , puis sélectionnez **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Recherchez le modèle de projet d' **application WPF** C# et suivez les étapes pour créer le projet, en nommant le projet **AdventureWorksProductsEditor**.

::: moniker-end

   Visual Studio crée le projet AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Créer un jeu de données pour l’application

Avant de pouvoir créer des contrôles liés aux données, vous devez définir un modèle de données pour votre application et l’ajouter à la fenêtre **Sources de données**. Dans cette procédure pas à pas, vous allez créer un dataset à utiliser comme modèle de données.

1. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

   La fenêtre **Sources de données** s’ouvre.

2. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

   L’Assistant **configuration de source de données** s’ouvre.

3. Dans la page **Choisir un type de source de données**, sélectionnez **Base de données**, puis cliquez sur **Suivant**.

4. Dans la page **Choisir un modèle de base de données**, sélectionnez **Groupe de données**, puis cliquez sur **Suivant**.

5. Dans la page **Choisir votre connexion de données**, sélectionnez une des options suivantes :

   - Si une connexion de données à l’exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la, puis cliquez sur **Suivant**.

   - Cliquez sur **Nouvelle connexion** et créez une connexion à la base de données AdventureWorksLT.

6. Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application**, cochez la case **Oui, enregistrer la connexion en tant que**, puis cliquez sur **Suivant**.

7. Dans la page **Choisir vos objets de base de données**, développez **Tables**, puis sélectionnez la table **Product (SalesLT)**.

8. Cliquez sur **Terminer**.

   Visual Studio ajoute un nouveau `AdventureWorksLTDataSet.xsd` fichier au projet et ajoute un élément **AdventureWorksLTDataSet** correspondant à la fenêtre sources de **données** . Le `AdventureWorksLTDataSet.xsd` fichier définit un DataSet typé nommé `AdventureWorksLTDataSet` et un TableAdapter nommé `ProductTableAdapter` . Plus loin dans cette procédure pas à pas, vous allez utiliser le `ProductTableAdapter` pour remplir le dataset avec des données et enregistrer les modifications dans la base de données.

9. Créez le projet.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modifier la méthode de remplissage par défaut du TableAdapter

Pour remplir le dataset avec des données, utilisez la méthode `Fill` du `ProductTableAdapter`. Par défaut, la méthode `Fill` remplit le `ProductDataTable` du `AdventureWorksLTDataSet` avec toutes les lignes de données de la table Product. Vous pouvez modifier cette méthode pour qu'elle ne retourne qu'un sous-ensemble des lignes. Pour cette procédure pas à pas, modifiez la méthode `Fill` pour ne retourner que les lignes des produits qui disposent de photos.

1. Dans l’**Explorateur de solutions**, double-cliquez sur le fichier *AdventureWorksLTDataSet.xsd*.

     Le Concepteur de DataSet s'ouvre.

2. Dans le concepteur, cliquez avec le bouton droit sur la requête **Fill**, **GetData()** et sélectionnez **Configurer**.

     L’Assistant **Configuration de TableAdapter** s’ouvre.

3. Dans la page **Entrer une instruction SQL**, ajoutez la clause WHERE suivante après l’instruction `SELECT` dans la zone de texte.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Cliquez sur **Terminer**.

## <a name="define-the-user-interface"></a>Définir l’interface utilisateur

Ajoutez plusieurs boutons à la fenêtre en modifiant le code XAML dans le Concepteur WPF. Plus loin dans cette procédure pas à pas, vous allez ajouter du code permettant aux utilisateurs de parcourir les produits et d'enregistrer les modifications apportées à ces derniers à l'aide de ces boutons.

1. Dans l’**Explorateur de solutions**, double-cliquez sur *MainWindow.xaml*.

    La fenêtre s’ouvre dans le **Concepteur WPF**.

2. Dans la vue [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] du concepteur, ajoutez le code suivant entre les étiquettes `<Grid>` :

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Créez le projet.

## <a name="create-data-bound-controls"></a>Créer des contrôles liés aux données

Créez des contrôles qui affichent les enregistrements des clients en faisant glisser la `Product` table de la fenêtre **sources de données** vers le Concepteur WPF.

1. Dans la fenêtre **Sources de données**, cliquez sur le menu déroulant pour le nœud **Product** et sélectionnez **Détails**.

2. Développez le nœud **Product**.

3. Pour cet exemple, certains champs ne vont pas s’afficher. Cliquez alors sur le menu déroulant situé à côté des nœuds suivants, puis sélectionnez **Aucun** :

    - IDCatégorieProduit

    - IDModèleProduit

    - NomFichierPhotoMiniature

    - rowguid

    - DateModification

4. Cliquez sur le menu déroulant à côté du nœud **ThumbNailPhoto** et sélectionnez **Image**.

    > [!NOTE]
    > Par défaut, les éléments de la fenêtre **Sources de données** représentant des images ont leur contrôle par défaut défini sur **Aucun**. En effet, les images sont stockées en tant que tableaux d'octets dans les bases de données et les tableaux d'octets peuvent contenir aussi bien un simple tableau d'octets que le fichier exécutable d'une application volumineuse.

5. Dans la fenêtre **Sources de données**, faites glisser le nœud **Product** vers la ligne de la grille située en dessous de la ligne contenant les boutons.

     Visual Studio génère du XAML qui définit un ensemble de contrôles liés aux données de la table **Product**. Il génère également du code qui charge les données. Pour plus d’informations sur le code XAML et le code générés, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Dans le concepteur, cliquez sur la zone de texte à côté de l’étiquette **Product ID**.

7. Dans la fenêtre **Propriétés**, cochez la case en regard de la propriété **IsReadOnly**.

## <a name="navigate-product-records"></a>Parcourir les enregistrements de produit

Ajoutez du code qui permet aux utilisateurs de faire défiler les enregistrements de produits à l’aide des **\<** and **>** boutons.

1. Dans le concepteur, double-cliquez sur le **<** bouton sur l’aire de la fenêtre.

     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `backButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Modifiez le gestionnaire d’événements `Window_Loaded`, de sorte que `ProductViewSource`, `AdventureWorksLTDataSet` et `AdventureWorksLTDataSetProductTableAdapter` se trouvent en dehors de la méthode et soient accessibles par tout le formulaire. Déclarez-les uniquement pour être globaux au formulaire, et assignez-les dans le `Window_Loaded` Gestionnaire d’événements similaire à ce qui suit :

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Ajoutez le code suivant au gestionnaire d'événements `backButton_Click` :

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Revenez au concepteur et double-cliquez sur le **>** bouton.

5. Ajoutez le code suivant au gestionnaire d'événements `nextButton_Click` :

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Enregistrer les modifications apportées aux enregistrements de produits

Ajoutez du code permettant aux utilisateurs d’enregistrer les modifications apportées aux enregistrements de produit à l’aide du bouton **Enregistrer les modifications**.

1. Dans le concepteur, double-cliquez sur le bouton **enregistrer les modifications** .

     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `saveButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Ajoutez le code suivant au gestionnaire d'événements `saveButton_Click` :

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > Cet exemple utilise la méthode `Save` de `TableAdapter` pour enregistrer les modifications. Cela nous convient dans cette procédure pas à pas, car une seule table de données est modifiée. Si vous devez enregistrer des modifications dans plusieurs tables de données, utilisez plutôt la méthode `UpdateAll` de `TableAdapterManager` générée par Visual Studio avec votre dataset. Pour plus d’informations, consultez [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Tester l’application

Générez et exécutez l’application. Vérifiez que vous pouvez afficher et mettre à jour les enregistrements produit.

1. Appuyez sur **F5**.

     L'application se génère et s'exécute. Vérifiez les éléments suivants :

    - Les zones de texte affichent les données du premier enregistrement produit qui dispose d'une photo. Ce produit a l’ID de produit 713 et le nom **Long-Sleeve Logo Jersey, S**.

    - Vous pouvez cliquer sur **>** les **<** boutons ou pour naviguer dans d’autres enregistrements de produits.

2. Dans un des enregistrements de produit, modifiez la valeur de **Size**, puis cliquez sur **Enregistrer les modifications**.

3. Fermez l’application, puis redémarrez-la en appuyant sur **F5** dans Visual Studio.

4. Accédez à l'enregistrement produit que vous avez modifié et vérifiez que la modification a été appliquée.

5. Fermez l'application.

## <a name="next-steps"></a>Étapes suivantes

À l’issue de cette procédure pas à pas, vous pouvez essayer les tâches associées suivantes :

- Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour lier des contrôles WPF à d’autres types de sources de données. Pour plus d’informations, consultez [lier des contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour afficher des données associées (c’est-à-dire des données dans une relation parent-enfant) dans des contrôles WPF. Pour plus d’informations, consultez [procédure pas à pas : afficher des données connexes dans une application WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Vue d’ensemble de la liaison de données](/dotnet/desktop-wpf/data/data-binding-overview)
