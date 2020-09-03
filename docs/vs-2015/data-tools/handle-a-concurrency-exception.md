---
title: Gérer une exception d’accès concurrentiel | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670038"
---
# <a name="handle-a-concurrency-exception"></a>Gérer une exception d’accès concurrentiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les exceptions d’accès concurrentiel ( <xref:System.Data.DBConcurrencyException> ) sont déclenchées lorsque deux utilisateurs essaient de modifier les mêmes données dans une base de données en même temps. Dans cette procédure pas à pas, vous allez créer une application Windows qui illustre comment intercepter un <xref:System.Data.DBConcurrencyException> , localiser la ligne à l’origine de l’erreur et apprendre une stratégie de gestion de celui-ci.

 Cette procédure pas à pas vous guide tout au long du processus suivant :

1. Créez un projet d' **application Windows** .

2. Créez un nouveau jeu de données basé sur la `Customers` table Northwind.

3. Créez un formulaire avec un <xref:System.Windows.Forms.DataGridView> pour afficher les données.

4. Remplir un DataSet avec les données de la `Customers` table dans la base de données Northwind.

5. Utilisez [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) dans Visual Studio pour accéder directement à la `Customers` table de données et modifier un enregistrement.

6. Remplacez le même enregistrement par une autre valeur, mettez à jour le DataSet et tentez d’écrire les modifications dans la base de données, ce qui entraîne le déclenchement d’une erreur d’accès concurrentiel.

7. Interceptez l’erreur, puis affichez les différentes versions de l’enregistrement, en permettant à l’utilisateur de déterminer s’il doit continuer et mettre à jour la base de données, ou pour annuler la mise à jour.

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à l’exemple de base de données Northwind avec l’autorisation d’effectuer des mises à jour.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l’aide en fonction de vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Création d'un projet
 Vous commencez votre procédure pas à pas en créant une nouvelle application Windows.

#### <a name="to-create-a-new-windows-application-project"></a>Pour créer un projet d’application Windows

1. Dans le menu **fichier** , créez un nouveau projet.

2. Dans le volet **types de projets** , sélectionnez un langage de programmation.

3. Dans le volet **Modèles**, sélectionnez **Application Windows**.

4. Nommez le projet `ConcurrencyWalkthrough` , puis sélectionnez **OK**.

     Visual Studio ajoute le projet à **Explorateur de solutions** et affiche un nouveau formulaire dans le concepteur.

## <a name="create-the-northwind-dataset"></a>Créer le jeu de données Northwind
 Dans cette section, vous allez créer un jeu de données nommé `NorthwindDataSet` .

#### <a name="to-create-the-northwinddataset"></a>Pour créer NorthwindDataSet

1. Dans le menu **données** , choisissez **Ajouter une nouvelle source de données**.

     L' [Assistant Configuration de source de données](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) s’ouvre.

2. Dans l’écran **choisir un type de source de données**, sélectionnez **base de**données.

3. Sélectionnez une connexion à l’exemple de base de données Northwind dans la liste des connexions disponibles. Si la connexion n’est pas disponible dans la liste des connexions, sélectionnez**nouvelle connexion** .

    > [!NOTE]
    > Si vous vous connectez à un fichier de base de données local, sélectionnez **non** lorsque vous y êtes invité si vous souhaitez ajouter le fichier à votre projet.

4. Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application**, sélectionnez **suivant**.

5. Développez le nœud **tables** et sélectionnez la `Customers` table. Le nom par défaut du jeu de données doit être `NorthwindDataSet` .

6. Sélectionnez **Terminer** pour ajouter le jeu de données au projet.

## <a name="create-a-data-bound-datagridview-control"></a>Créer un contrôle DataGridView lié aux données
 Dans cette section, vous créez un <xref:System.Windows.Forms.DataGridView> en faisant glisser l’élément **Customers** de la fenêtre **sources de données** vers votre Windows Form.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Pour créer un contrôle DataGridView lié à la table Customers

1. Dans le menu **données** , choisissez **afficher les sources** de données pour ouvrir la **fenêtre sources de données**.

2. Dans la fenêtre **sources de données** , développez le nœud **NorthwindDataSet** , puis sélectionnez la table **Customers** .

3. Sélectionnez la flèche vers le bas sur le nœud de la table, puis sélectionnez **DataGridView** dans la liste déroulante.

4. Faites glisser la table sur une zone vide de votre formulaire.

     Un <xref:System.Windows.Forms.DataGridView> contrôle nommé `CustomersDataGridView` et un <xref:System.Windows.Forms.BindingNavigator> nommé `CustomersBindingNavigator` sont ajoutés au formulaire qui est lié au <xref:System.Windows.Forms.BindingSource> . Dans, il est à son tour lié à la `Customers` table dans le `NorthwindDataSet` .

## <a name="test-the-form"></a>Tester le formulaire
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu jusqu’à ce point.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

1. Appuyez sur **F5** pour exécuter l’application

     Le formulaire s’affiche avec un <xref:System.Windows.Forms.DataGridView> contrôle qui est rempli avec les données de la `Customers` table.

2. Dans le menu **Déboguer** , sélectionnez**arrêter le débogage**.

## <a name="handleconcurrency-errors"></a>Erreurs Handleconcurrency
 La façon dont vous gérez les erreurs dépend des règles d’entreprise spécifiques qui régissent votre application. Pour cette procédure pas à pas, nous utilisons la stratégie suivante comme exemple pour tohandle l’erreur d’accès concurrentiel.

 Le applicationpresents l’utilisateur avec trois versions de l’enregistrement :

- Enregistrement actif dans la base de données

- Enregistrement d’origine chargé dans le jeu de données

- Modifications proposées dans le DataSet

  L’utilisateur est alors en mesure de remplacer la base de données par la version proposée, ou d’annuler la mise à jour et d’actualiser le DataSet avec les nouvelles valeurs de la base de données.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Pour activer la gestion des erreurs d’accès concurrentiel

1. Créez un gestionnaire d’erreurs personnalisé.

2. Affichez les choix à l’utilisateur.

3. Traitez la réponse de l’utilisateur.

4. Renvoyez la mise à jour ou réinitialisez les données dans le DataSet.

### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode pour gérer l’exception d’accès concurrentiel
 Lorsque vous tentez d’effectuer une mise à jour et qu’une exception est levée, vous souhaitez généralement effectuer une opération avec les informations fournies par l’exception levée.

 Dans cette section, vous allez ajouter du code qui tente de mettre à jour la base de données. Vous gérez également tout <xref:System.Data.DBConcurrencyException> ce qui peut être déclenché, ainsi que toutes les autres exceptions.

> [!NOTE]
> Les `CreateMessage` `ProcessDialogResults` méthodes et seront ajoutées plus loin dans cette procédure pas à pas.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Pour ajouter la gestion des erreurs pour l’erreur d’accès concurrentiel

1. Ajoutez le code suivant sous la `Form1_Load` méthode :

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Remplacez la `CustomersBindingNavigatorSaveItem_Click` méthode pour appeler la `UpdateDatabase` méthode afin qu’elle ressemble à ce qui suit :

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices à l’utilisateur
 Le code que vous venez d’écrire appelle la `CreateMessage` procédure pour afficher les informations d’erreur à l’utilisateur. Pour cette procédure pas à pas, vous utilisez une boîte de message pour afficher les différentes versions de l’enregistrement à l’utilisateur. Cela permet à l’utilisateur de choisir s’il faut remplacer l’enregistrement par les modifications ou d’annuler la modification. Une fois que l’utilisateur a sélectionné une option (clique sur un bouton) dans la boîte de message, la réponse est transmise à la `ProcessDialogResult` méthode.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Pour créer le message à afficher à l’utilisateur

- Créez le message en ajoutant le code suivant à l' **éditeur de code**. Entrez ce code sous la `UpdateDatabase` méthode.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Traiter la réponse de l’utilisateur
 Vous avez également besoin de code pour traiter la réponse de l’utilisateur à la boîte de message. Les options sont soit pour remplacer l’enregistrement en cours dans la base de données avec la modification proposée, soit pour abandonner les modifications locales et actualiser la table de données avec l’enregistrement qui se trouve actuellement dans la base de données. Si l’utilisateur choisit Oui, la <xref:System.Data.DataTable.Merge%2A> méthode est appelée avec l’argument *preserveChanges* défini sur `true` . Cela entraîne la réussite de la tentative de mise à jour, car la version d’origine de l’enregistrement correspond maintenant à l’enregistrement dans la base de données.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Pour traiter l’entrée d’utilisateur à partir de la boîte de message

- Ajoutez le code suivant sous le code qui a été ajouté dans la section précédente.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Tester le formulaire
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu. Pour simuler une violation d’accès concurrentiel, vous devez modifier les données dans la base de données après avoir rempli le NorthwindDataSet.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

1. Appuyez sur **F5** pour exécuter l’application.

2. Une fois que le formulaire s’affiche, laissez-le s’exécuter et basculez vers l’IDE de Visual Studio.

3. Dans le menu **Affichage**, cliquez sur **Explorateur de serveurs**.

4. Dans **Explorateur de serveurs**, développez la connexion que votre application utilise, puis développez le nœud **tables** .

5. Cliquez avec le bouton droit sur la table **Customers** , puis sélectionnez **afficher les données**de la table.

6. Dans le premier enregistrement ( `ALFKI` ), remplacez `ContactName` par `Maria Anders2` .

    > [!NOTE]
    > Accédez à une autre ligne pour valider la modification.

7. Basculez vers le `ConcurrencyWalkthrough` formulaire en cours d’exécution.

8. Dans le premier enregistrement du formulaire ( `ALFKI` ), remplacez `ContactName` par `Maria Anders1` .

9. Sélectionnez le bouton **Enregistrer**.

     L’erreur d’accès concurrentiel est déclenchée et la boîte de message s’affiche.

10. Si vous sélectionnez **non** , la mise à jour est annulée et le jeu de données est mis à jour avec les valeurs qui se trouvent actuellement dans la base de données. Si vous sélectionnez **Oui** , la valeur proposée est écrite dans la base de données.

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)