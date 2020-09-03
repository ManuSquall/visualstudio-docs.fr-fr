---
title: Enregistrer des données avec les méthodes DBDirect du TableAdapter | Microsoft Docs
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655419"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Enregistrer des données avec les méthodes DBDirect du TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas fournit des instructions détaillées pour exécuter des instructions SQL directement sur une base de données à l’aide des méthodes DBDirect d’un TableAdapter. Les méthodes DBDirect d’un TableAdapter fournissent un niveau élevé de contrôle sur vos mises à jour de base de données. Vous pouvez les utiliser pour exécuter des instructions SQL et des procédures stockées spécifiques en appelant `Insert` les `Update` méthodes individuelles, et selon les `Delete` besoins de votre application (par opposition à la méthode surchargée `Update` qui exécute les instructions Update, INSERT et Delete dans un seul appel).

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Créez une nouvelle **application Windows**.

- Créez et configurez un DataSet à l’aide de l' [Assistant Configuration de source de données](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Sélectionner le contrôle à créer dans le formulaire lors du déplacement d’éléments depuis la fenêtre **Sources de données**. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Créer un formulaire lié aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** sur le formulaire.

- Ajoutez des méthodes pour accéder directement à la base de données et effectuer des insertions, des mises à jour et des suppressions.

## <a name="prerequisites"></a>Prérequis
 Pour réaliser cette procédure pas à pas, vous aurez besoin des éléments suivants :

- avoir accès à l'exemple de base de données Northwind.

## <a name="create-a-windows-application"></a>Créer une application Windows
 La première étape consiste à créer une **application Windows**.

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, dans le menu **fichier** , créez un nouveau **projet**.

2. Nommez le projet **TableAdapterDbDirectMethodsWalkthrough**.

3. Sélectionnez **application Windows**, puis cliquez sur **OK**. Pour plus d’informations, consultez [applications clientes](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Le projet **TableAdapterDbDirectMethodsWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données
 Cette étape utilise l’**Assistant Configuration de source de données** pour créer une source de données basée sur la table `Region` de l’exemple de base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Dans le menu **données** , sélectionnez **afficher les sources de données**.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’**Assistant Configuration de source de données**.

3. Dans l’écran **choisir un type de source de données** , sélectionnez **base de**données, puis sélectionnez **suivant**.

4. Sur l’écran **choisir votre connexion de données** , effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

         -ou-

    - Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données requiert un mot de passe, sélectionnez l’option permettant d’inclure des données sensibles, puis sélectionnez **suivant**.

6. Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , sélectionnez **suivant**.

7. Dans l’écran **choisir vos objets de base de données** , développez le nœud **tables** .

8. Sélectionnez la `Region` table, puis sélectionnez **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et la table `Region` apparaît dans la fenêtre **Sources de données**.

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols au formulaire pour afficher les données
 Créez les contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **Sources de données** sur votre formulaire.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Pour créer des contrôles liés aux données dans le Windows Form

- Faites glisser le nœud **région** principale de la fenêtre **sources de données** vers le formulaire.

     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent dans le formulaire. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d’état des composants.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Pour ajouter des boutons pour appeler les méthodes DbDirect individuelles de TableAdapter

1. Faites glisser trois contrôles <xref:System.Windows.Forms.Button> depuis la **Boîte à outils** vers **Form1** (sous la **RegionDataGridView**).

2. Définissez les propriétés **Name** et **Text** suivantes sur chaque bouton.

    |Nom|Texte|
    |----------|----------|
    |`InsertButton`|**Insérer**|
    |`UpdateButton`|**Mettre à jour**|
    |`DeleteButton`|**Supprimer**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Pour ajouter du code afin d'insérer de nouveaux enregistrements dans la base de données

1. Sélectionnez **InsertButton** pour créer un gestionnaire d’événements pour l’événement Click et ouvrir votre formulaire dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `InsertButton_Click` par le code suivant :

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Pour ajouter du code afin de mettre à jour des enregistrements dans la base de données

1. Double-cliquez sur **UpdateButton** pour créer un gestionnaire d’événements pour l’événement Click et ouvrir votre formulaire dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `UpdateButton_Click` par le code suivant :

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Pour ajouter du code afin de supprimer des enregistrements de la base de données

1. Sélectionnez **DeleteButton** pour créer un gestionnaire d’événements pour l’événement Click et ouvrir votre formulaire dans l’éditeur de code.

2. Remplacez le gestionnaire d'événements `DeleteButton_Click` par le code suivant :

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Exécution de l'application

#### <a name="to-run-the-application"></a>Pour exécuter l’application

- Appuyez sur **F5** pour exécuter l’application.

- Sélectionnez le bouton **Insérer** et vérifiez que le nouvel enregistrement apparaît dans la grille.

- Sélectionnez le bouton **mettre à jour** et vérifiez que l’enregistrement est mis à jour dans la grille.

- Sélectionnez le bouton **supprimer** , puis vérifiez que l’enregistrement est supprimé de la grille.

## <a name="next-steps"></a>Étapes suivantes
 Selon les exigences de votre application, vous pouvez effectuer plusieurs étapes après la création d’un formulaire lié aux données. Vous pouvez apporter à cette procédure pas à pas les améliorations suivantes :

- Ajout d'une fonctionnalité de recherche au formulaire. Pour plus d’informations, consultez [Comment : ajouter une requête paramétrable à une Application Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Ajout de tables supplémentaires au dataset en sélectionnant **Configurer le DataSet à l’aide de l’Assistant** dans la fenêtre **Sources de données**. Vous pouvez ajouter des contrôles pour afficher les données associées en faisant glisser les nœuds associés vers le formulaire.

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
