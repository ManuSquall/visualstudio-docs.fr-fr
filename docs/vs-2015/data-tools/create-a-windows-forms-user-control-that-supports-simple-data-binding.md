---
title: Créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf30a38384863c9ba5a8af35af3326a51058d831
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668771"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Créer un contrôle utilisateur Windows Forms prenant en charge la liaison de données simples
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour présenter des données dans des formulaires d’applications Windows, vous pouvez choisir des contrôles existants dans la **Boîte à outils** ou créer des contrôles personnalisés si votre application nécessite des fonctionnalités qui ne sont pas disponibles dans les contrôles standard. Cette procédure pas à pas vous indique comment créer un contrôle qui implémente l'objet <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Les contrôles qui implémentent <xref:System.ComponentModel.DefaultBindingPropertyAttribute> peuvent contenir une propriété pouvant être liée aux données. Ce type de contrôles est similaire à <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.

 Pour plus d’informations sur la création de contrôles, consultez [développement de contrôles Windows Forms au moment du design](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Quand vous créez des contrôles à utiliser dans des scénarios de liaison de données, vous devez implémenter l’un des attributs de liaison de données suivants :

|Utilisation des attributs de liaison de données|
|-----------------------------------|
|Implémentez <xref:System.ComponentModel.DefaultBindingPropertyAttribute> sur des contrôles simples, comme <xref:System.Windows.Forms.TextBox>, qui affichent une seule colonne (ou propriété) de données. (Ce processus est décrit dans cette page de procédure pas à pas.)|
|Implémentez <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.DataGridView>, qui affichent des listes (ou tables) de données. Pour plus d’informations, consultez [créer un Windows Forms contrôle utilisateur qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implémentez l'objet <xref:System.ComponentModel.LookupBindingPropertiesAttribute> sur des contrôles, comme <xref:System.Windows.Forms.ComboBox>, qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou propriété. Pour plus d’informations, consultez [créer un Windows Forms contrôle utilisateur qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Cette procédure pas à pas crée un contrôle simple qui affiche les données d'une seule colonne dans une table. Cet exemple utilise la colonne `Phone` de la table `Customers` de l'exemple de base de données Northwind. Le contrôle utilisateur simple affichera les numéros de téléphone des clients dans un format de numéro de téléphone standard, à l’aide d’un <xref:System.Windows.Forms.MaskedTextBox> et en définissant le masque sur un numéro de téléphone.

 Pendant cette procédure pas à pas, vous allez apprendre à :

- Créez une nouvelle **application Windows**.

- Ajouter un nouveau **Contrôle utilisateur** à votre projet.

- Concevoir visuellement le contrôle utilisateur.

- Implémenter l'attribut `DefaultBindingProperty`.

- Créez un DataSet à l’aide de l’Assistant **configuration de source de données** .

- Définir la colonne **Phone** dans la fenêtre **Sources de données** pour qu’elle utilise le nouveau contrôle.

- Créer un formulaire pour afficher des données dans le nouveau contrôle.

## <a name="prerequisites"></a>Configuration requise
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- avoir accès à l'exemple de base de données Northwind.

## <a name="create-a-windows-application"></a>Créer une application Windows
 La première étape consiste à créer une **application Windows**.

#### <a name="to-create-the-new-windows-project"></a>Pour créer un projet Windows

1. Dans Visual Studio, dans le menu **fichier** , créez un nouveau **projet**.

2. Nommez le projet **SimpleControlWalkthrough**.

3. Sélectionnez **application Windows** , puis cliquez sur **OK**. Pour plus d’informations, consultez [applications clientes](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Le projet **SimpleControlWalkthrough** est créé et ajouté à l’**Explorateur de solutions**.

## <a name="add-a-user-control-to-the-project"></a>Ajouter un contrôle utilisateur au projet
 Cette procédure pas à pas crée un contrôle simple pouvant être lié aux données à partir d’un **contrôle utilisateur**. Ajoutez donc un élément de **contrôle utilisateur** au projet **SimpleControlWalkthrough** .

#### <a name="to-add-a-user-control-to-the-project"></a>Pour ajouter un contrôle utilisateur au projet

1. Dans le menu **Projet**, choisissez **Ajouter un contrôle utilisateur**.

2. Tapez `PhoneNumberBox` dans la zone Nom, puis cliquez sur **Ajouter**.

     Le contrôle **PhoneNumberBox** est ajouté à l’**Explorateur de solutions** et s’ouvre dans le concepteur.

## <a name="design-the-phonenumberbox-control"></a>Concevoir le contrôle PhoneNumberBox
 Cette procédure pas à pas développe le <xref:System.Windows.Forms.MaskedTextBox> existant pour créer le contrôle `PhoneNumberBox`.

#### <a name="to-design-the-phonenumberbox-control"></a>Pour concevoir le contrôle PhoneNumberBox

1. Faites glisser un <xref:System.Windows.Forms.MaskedTextBox> depuis la **Boîte à outils** vers l’aire de conception du contrôle utilisateur.

2. Sélectionnez la balise active du <xref:System.Windows.Forms.MaskedTextBox> que vous venez de faire glisser et choisissez **Définir le masque**.

3. Sélectionnez **Numéro de téléphone** dans la boîte de dialogue **Masque de saisie** et cliquez sur **OK** pour définir le masque.

## <a name="add-the-required-data-binding-attribute"></a>Ajouter l’attribut de liaison de données requis
 Pour des contrôles simples prenant en charge la liaison de données, implémentez l'attribut <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Pour implémenter l'attribut DefaultBindingProperty

1. Basculez le contrôle `PhoneNumberBox` sur le mode Code. (Dans le menu **Affichage**, choisissez **Code**.)

2. Remplacez le code de `PhoneNumberBox` par le code suivant :

     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]

3. Dans le menu **Générer** , cliquez sur **Générer la solution**.

## <a name="create-a-data-source-from-your-database"></a>Créer une source de données à partir de votre base de données
 Cette étape utilise l’Assistant **Configuration de source de données** pour créer une source de données basée sur la table `Customers` de l’exemple de base de données Northwind. Vous devez avoir accès à l'exemple de base de données Northwind pour créer la connexion.

#### <a name="to-create-the-data-source"></a>Pour créer la source de données

1. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

2. Dans la fenêtre **Sources de données**, sélectionnez **Ajouter une nouvelle source de données** pour démarrer l’Assistant **Configuration de source de données**.

3. Dans la page **Choisir un type de source de données**, sélectionnez **Base de données**, puis cliquez sur **Suivant**.

4. Dans la page **Choisir votre connexion de données**, effectuez l’une des opérations suivantes :

    - Si une connexion de données à l’exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.

    - Sélectionnez **Nouvelle connexion** pour afficher la boîte de dialogue **Ajouter/Modifier la connexion**.

5. Si votre base de données nécessite un mot de passe, sélectionnez l’option pour inclure les données sensibles, puis cliquez sur **Suivant**.

6. Dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , cliquez sur **suivant**.

7. Dans la page **Choisir vos objets de base de données**, développez le nœud **Tables**.

8. Sélectionnez la table `Customers`, puis cliquez sur **Terminer**.

     **NorthwindDataSet** est ajouté à votre projet et la table `Customers` apparaît dans la fenêtre **Sources de données**.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Définir la colonne Phone pour qu’elle utilise le contrôle PhoneNumberBox
 Dans la fenêtre **Sources de données**, vous pouvez définir le contrôle à créer avant de faire glisser des éléments vers votre formulaire.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Pour définir la colonne Phone pour qu'elle soit liée au contrôle PhoneNumberBox

1. Ouvrez **Form1** dans le concepteur.

2. Développez le nœud **Customers** dans la fenêtre **Sources de données**.

3. Cliquez sur la flèche déroulante du nœud **Customers** et choisissez **Détails** dans la liste de contrôles.

4. Cliquez sur la flèche déroulante de la colonne **Phone** et choisissez **Personnaliser**.

5. Sélectionnez **PhoneNumberBox** dans la liste des **Contrôles associés** de la boîte de dialogue **Options de personnalisation de l’interface utilisateur de données**.

6. Cliquez sur la flèche déroulante de la colonne **Phone** et choisissez **PhoneNumberBox**.

## <a name="addcontrols-to-the-form"></a>Addcontrols au formulaire
 Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis la fenêtre **Sources de données** vers le formulaire.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Pour créer des contrôlés liés aux données dans le formulaire

- Faites glisser le nœud **Customers** principal depuis la fenêtre **sources de données** vers le formulaire et vérifiez que le contrôle `PhoneNumberBox` est utilisé pour afficher les données dans la colonne `Phone`.

     Les contrôles liés aux données assortis d'étiquettes descriptives apparaissent dans le formulaire, ainsi qu'une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état des composants.

## <a name="run-the-application"></a>Exécuter l'application

#### <a name="to-run-the-application"></a>Pour exécuter l’application

- Appuyez sur F5 pour exécuter l'application.

## <a name="next-steps"></a>Étapes suivantes
 Selon les spécifications de votre application, vous pouvez exécuter différentes étapes après la création d'un contrôle prenant en charge la liaison de données. Les étapes ultérieures sont habituellement celles-ci :

- Positionnement de vos contrôles personnalisés dans une bibliothèque de contrôles pour pouvoir les réutiliser dans d'autres applications.

- Création de contrôles prenant en charge des scénarios de liaison de données plus complexes. Pour plus d’informations, consultez [créer un Windows Forms contrôle utilisateur qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) et [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
