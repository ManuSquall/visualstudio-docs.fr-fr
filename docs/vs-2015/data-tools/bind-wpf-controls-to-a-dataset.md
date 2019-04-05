---
title: Lier des contrôles WPF à un jeu de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94b6c5d7e1695b4b9ef2d1b383575a8806b112db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951354"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Lier des contrôles WPF à un dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dans cette procédure pas à pas, vous allez créer une application WPF qui contient des contrôles liés aux données. Les contrôles sont liés aux enregistrements produit encapsulés dans un dataset. Vous allez également ajouter des boutons pour parcourir les produits et enregistrer les modifications apportées aux enregistrements produit.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
- création d'une application WPF et d'un dataset généré à partir des données de l'exemple de base de données AdventureWorksLT ;  
  
- création d’un ensemble de contrôles liés aux données en faisant glisser une table de données depuis la fenêtre **Sources de données** vers une fenêtre du Concepteur WPF ;  
  
- création de boutons permettant d'avancer et de reculer dans les enregistrements produit ;  
  
- création d'un bouton permettant d'enregistrer les modifications effectuées par les utilisateurs sur les enregistrements produit dans la table de données et la source de données sous-jacente.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT. Vous pouvez télécharger la base de données AdventureWorksLT à partir de la [site CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :  
  
- Datasets et TableAdapters. Pour plus d’informations, consultez [outils de Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
- Utilisation du Concepteur WPF. Pour plus d’informations, consultez [WPF et Silverlight Designer Overview](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Liaison de données WPF. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Créer le projet  
 Créez un projet WPF. Le projet affichera les enregistrements produit.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Développez **Visual Basic** ou **Visual C#**, puis sélectionnez **Windows**.  
  
4.  Sélectionnez le modèle de projet **Application WPF**.  
  
5.  Dans le **nom** , tapez `AdventureWorksProductsEditor` et cliquez sur **OK**.  
  
     Visual Studio crée le `AdventureWorksProductsEditor` projet.  
  
## <a name="create-a-dataset-for-the-application"></a>Créer un jeu de données pour l’application  
 Avant de pouvoir créer des contrôles liés aux données, vous devez définir un modèle de données pour votre application et l’ajouter à la fenêtre **Sources de données**. Dans cette procédure pas à pas, vous allez créer un dataset à utiliser comme modèle de données.  
  
#### <a name="to-create-a-dataset"></a>Pour créer un dataset  
  
1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
     La fenêtre **Sources de données** s’ouvre.  
  
2.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
     L’Assistant **Configuration de source de données** s’ouvre.  
  
3.  Dans la page **Choisir un type de source de données**, sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir un modèle de base de données**, sélectionnez **Groupe de données**, puis cliquez sur **Suivant**.  
  
5.  Dans la page **Choisir votre connexion de données**, sélectionnez une des options suivantes :  
  
    -   Si une connexion de données à l’exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la, puis cliquez sur **Suivant**.  
  
    -   Cliquez sur **Nouvelle connexion** et créez une connexion à la base de données AdventureWorksLT.  
  
6.  Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application**, cochez la case **Oui, enregistrer la connexion en tant que**, puis cliquez sur **Suivant**.  
  
7.  Dans la page **Choisir vos objets de base de données**, développez **Tables**, puis sélectionnez la table **Product (SalesLT)**.  
  
8.  Cliquez sur **Terminer**.  
  
     Visual Studio ajoute un nouveau fichier AdventureWorksLTDataSet.xsd au projet, et il ajoute un correspondant **AdventureWorksLTDataSet** d’élément à la **des Sources de données** fenêtre. Le fichier AdventureWorksLTDataSet.xsd définit un dataset typé nommé `AdventureWorksLTDataSet` et un TableAdapter nommé `ProductTableAdapter`. Plus loin dans cette procédure pas à pas, vous allez utiliser le `ProductTableAdapter` pour remplir le dataset avec des données et enregistrer les modifications dans la base de données.  
  
9. Générez le projet.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Modifier la méthode de remplissage par défaut du TableAdapter  
 Pour remplir le dataset avec des données, utilisez la méthode `Fill` du `ProductTableAdapter`. Par défaut, la méthode `Fill` remplit le `ProductDataTable` du `AdventureWorksLTDataSet` avec toutes les lignes de données de la table Product. Vous pouvez modifier cette méthode pour qu'elle ne retourne qu'un sous-ensemble des lignes. Pour cette procédure pas à pas, modifiez la méthode `Fill` pour ne retourner que les lignes des produits qui disposent de photos.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Pour charger les lignes des produits disposant de photos  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le fichier AdventureWorksLTDataSet.xsd.  
  
     Le Concepteur de DataSet s'ouvre.  
  
2.  Dans le concepteur, cliquez sur le **Fill,GetData()** de requête et sélectionnez **configurer**.  
  
     L’Assistant **Configuration de TableAdapter** s’ouvre.  
  
3.  Dans la page **Entrer une instruction SQL**, ajoutez la clause WHERE suivante après l’instruction `SELECT` dans la zone de texte.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Cliquez sur **Terminer**.  
  
## <a name="define-the-user-interface"></a>Définir l’interface utilisateur  
 Ajoutez plusieurs boutons à la fenêtre en modifiant le code XAML dans le Concepteur WPF. Plus loin dans cette procédure pas à pas, vous allez ajouter du code permettant aux utilisateurs de parcourir les produits et d'enregistrer les modifications apportées à ces derniers à l'aide de ces boutons.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Pour définir l'interface utilisateur de la fenêtre  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur MainWindow.xaml.  
  
     La fenêtre s'ouvre dans le Concepteur WPF.  
  
2.  Dans la vue [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] du concepteur, ajoutez le code suivant entre les étiquettes `<Grid>` :  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Générez le projet.  
  
## <a name="createdata-bound-controls"></a>Contrôles liés aux ignorant  
 Créer des contrôles qui affichent les enregistrements client en faisant glisser le `Product` table à partir de la **des Sources de données** fenêtre vers le Concepteur WPF.  
  
#### <a name="to-create-data-bound-controls"></a>Pour créer des contrôles liés aux données  
  
1.  Dans la fenêtre **Sources de données**, cliquez sur le menu déroulant pour le nœud **Product** et sélectionnez **Détails**.  
  
2.  Développez le nœud **Product**.  
  
3.  Pour cet exemple, certains champs ne vont pas s’afficher. Cliquez alors sur le menu déroulant situé à côté des nœuds suivants, puis sélectionnez **Aucun** :  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Cliquez sur le menu déroulant à côté du nœud **ThumbNailPhoto** et sélectionnez **Image**.  
  
    > [!NOTE]
    >  Par défaut, les éléments de la fenêtre **Sources de données** représentant des images ont leur contrôle par défaut défini sur **Aucun**. En effet, les images sont stockées en tant que tableaux d'octets dans les bases de données et les tableaux d'octets peuvent contenir aussi bien un simple tableau d'octets que le fichier exécutable d'une application volumineuse.  
  
5.  Dans la fenêtre **Sources de données**, faites glisser le nœud **Product** vers la ligne de la grille située en dessous de la ligne contenant les boutons.  
  
     Visual Studio génère du XAML qui définit un ensemble de contrôles liés aux données de la table **Product**. Il génère également du code qui charge les données. Pour plus d’informations sur le XAML et le code généré, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Dans le concepteur, cliquez sur la zone de texte à côté de l’étiquette **Product ID**.  
  
7.  Dans la fenêtre **Propriétés**, cochez la case en regard de la propriété **IsReadOnly**.  
  
## <a name="navigating-product-records"></a>Parcourir les enregistrements de produit  
 Ajoutez du code permettant aux utilisateurs de parcourir les enregistrements de produit à l’aide des boutons **\<** et **>**.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Pour permettre aux utilisateurs de parcourir les enregistrements produit  
  
1.  Dans le concepteur, double-cliquez sur le bouton **<** de la fenêtre.  
  
     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `backButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Modifiez le gestionnaire d’événements `Window_Loaded`, de sorte que `ProductViewSource`, `AdventureWorksLTDataSet` et `AdventureWorksLTDataSetProductTableAdapter` se trouvent en dehors de la méthode et soient accessibles par tout le formulaire. Déclarez qu’uniquement soit global au formulaire et assignez-les dans le `Window_Loaded` Gestionnaire d’événements similaire à ce qui suit :  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3.  Ajoutez le code suivant au gestionnaire d'événements `backButton_Click` :  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4.  Revenez dans le concepteur et double-cliquez sur le bouton **>**.  
  
5.  Ajoutez le code suivant au gestionnaire d'événements `nextButton_Click` :  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>SaveChanges aux enregistrements produit  
 Ajoutez du code permettant aux utilisateurs d’enregistrer les modifications apportées aux enregistrements de produit à l’aide du bouton **Enregistrer les modifications**.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Pour ajouter la possibilité d'enregistrer les modifications apportées aux enregistrements produit  
  
1.  Dans le concepteur, double-cliquez sur le bouton **Enregistrer les modifications**.  
  
     Visual Studio ouvre le fichier code-behind et crée un gestionnaire d’événements `saveButton_Click` pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements `saveButton_Click` :  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    >  Cet exemple utilise la méthode `Save` de `TableAdapter` pour enregistrer les modifications. Cela nous convient dans cette procédure pas à pas, car une seule table de données est modifiée. Si vous devez enregistrer des modifications dans plusieurs tables de données, utilisez plutôt la méthode `UpdateAll` de `TableAdapterManager` générée par Visual Studio avec votre dataset. Pour plus d’informations, consultez [vue d’ensemble de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Tester l’application  
 Générez et exécutez l’application. Vérifiez que vous pouvez afficher et mettre à jour les enregistrements produit.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Appuyez sur **F5**.  
  
     L'application se génère et s'exécute. Vérifiez ce qui suit :  
  
    -   Les zones de texte affichent les données du premier enregistrement produit qui dispose d'une photo. Ce produit a l’ID de produit 713 et le nom **Long-Sleeve Logo Jersey, S**.  
  
    -   Vous pouvez cliquez sur les boutons **>** ou **<** pour parcourir les autres enregistrements de produit.  
  
2.  Dans un des enregistrements de produit, modifiez la valeur de **Size**, puis cliquez sur **Enregistrer les modifications**.  
  
3.  Fermez l’application, puis redémarrez-la en appuyant sur **F5** dans Visual Studio.  
  
4.  Accédez à l'enregistrement produit que vous avez modifié et vérifiez que la modification a été appliquée.  
  
5.  Fermez l'application.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois cette procédure pas à pas terminée, vous pouvez effectuer les tâches associées suivantes :  
  
-   Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour lier des contrôles WPF à d’autres types de sources de données. Pour plus d’informations, consultez [WPF de lier des contrôles à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Découvrez comment utiliser la fenêtre **Sources de données** dans Visual Studio pour afficher des données associées (c’est-à-dire des données dans une relation parent-enfant) dans des contrôles WPF. Pour plus d’informations, consultez [Procédure pas à pas : Affichage de données liées dans une Application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF et Silverlight Designer Overview](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Vue d’ensemble de la liaison de données](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
