---
title: Gérer une exception d’accès concurrentiel | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 616b837613e0e2c76330a68133929e6b85a94f98
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812931"
---
# <a name="handle-a-concurrency-exception"></a>Gérer une exception d’accès concurrentiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Exceptions d’accès concurrentiel (<xref:System.Data.DBConcurrencyException>) sont déclenchés lorsque deux utilisateurs tentent de modifier les mêmes données dans une base de données en même temps. Dans cette procédure pas à pas, vous créez une application Windows qui montre comment intercepter une <xref:System.Data.DBConcurrencyException>, localisez la ligne qui a provoqué l’erreur et découvrez une stratégie pour son traitement.  
  
 Cette procédure pas à pas vous accompagne tout au long du processus suivant :  
  
1.  Créer un nouveau **Windows Application** projet.  
  
2.  Créer un nouveau jeu de données basé sur Northwind `Customers` table.  
  
3.  Créer un formulaire avec un <xref:System.Windows.Forms.DataGridView> pour afficher les données.  
  
4.  Remplir un dataset avec des données à partir de la `Customers` table dans la base de données Northwind.  
  
5.  Utilisez le [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) dans Visual Studio pour accéder directement à la `Customers` de table de données et modifier un enregistrement.  
  
6.  Modifier le même enregistrement à une valeur différente, mettre à jour le jeu de données et essaient d’écrire les modifications dans la base de données, ce qui entraîne le déclenchement d’une erreur d’accès concurrentiel.  
  
7.  Intercepter l’erreur, puis afficher les différentes versions de l’enregistrement, permettant à l’utilisateur déterminer s’il faut continuer et mettre à jour de la base de données ou annuler la mise à jour.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Accès à la base de données Northwind avec l’autorisation d’effectuer des mises à jour. Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et commandes de menu affichées peuvent différer de celles décrites dans l’aide selon vos paramètres actifs ou de l’édition que vous utilisez. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Créer un nouveau projet  
 Pour commencer votre procédure pas à pas en créant une nouvelle application Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Pour créer un nouveau projet d’application Windows  
  
1.  Sur le **fichier** menu, créez un nouveau projet.  
  
2.  Dans le **Types de projets** volet, sélectionnez un langage de programmation.  
  
3.  Dans le **modèles** volet, sélectionnez **Windows Application**.  
  
4.  Nommez le projet `ConcurrencyWalkthrough`, puis sélectionnez**OK**.  
  
     Visual Studio ajoute le projet à **l’Explorateur de solutions** et affiche un nouveau formulaire dans le concepteur.  
  
## <a name="create-the-northwind-dataset"></a>Créer le jeu de données Northwind  
 Dans cette section, vous créez un dataset nommé `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Pour créer NorthwindDataSet  
  
1.  Sur le **données** menu, choisissez **ajouter nouvelle source de données**.  
  
     Le [Assistant de Configuration de Source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) s’ouvre.  
  
2.  Sur le **choisir un Type de Source de données**s’affiche, sélectionnez **base de données**.  
  
3.  Sélectionnez une connexion à la base de données Northwind dans la liste des connexions disponibles. Si la connexion n’est pas disponible dans la liste des connexions, sélectionnez**nouvelle connexion**  
  
    > [!NOTE]
    >  Si vous vous connectez à un fichier de base de données locale, sélectionnez **non** lorsque vous le feriez pour vous confirmer ajouter le fichier à votre projet.  
  
4.  Sur le **enregistrer la chaîne de connexion au fichier de configuration de l’application**s’affiche, sélectionnez **suivant**.  
  
5.  Développez le **Tables** nœud et sélectionnez le `Customers` table. Le nom par défaut pour le jeu de données doit être `NorthwindDataSet`.  
  
6.  Sélectionnez**Terminer** pour ajouter le jeu de données au projet.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Créer un contrôle de DataGridView lié aux données  
 Dans cette section, vous allez créer un <xref:System.Windows.Forms.DataGridView> en faisant glisser le **clients** d’élément à partir de la **des Sources de données** fenêtre sur votre formulaire Windows.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Pour créer un contrôle DataGridView lié à la table Customers  
  
1.  Sur le **données** menu, choisissez **afficher les Sources de données** pour ouvrir le **fenêtre Sources de données**.  
  
2.  Dans le **des Sources de données** fenêtre, développez le **NorthwindDataSet** nœud, puis sélectionnez le **clients** table.  
  
3.  Sélectionnez la flèche bas sur le nœud de la table, puis **DataGridView**dans la liste déroulante.  
  
4.  Faites glisser la table dans une zone vide de votre formulaire.  
  
     Un <xref:System.Windows.Forms.DataGridView> contrôle nommé `CustomersDataGridView` et un <xref:System.Windows.Forms.BindingNavigator> nommé `CustomersBindingNavigator` sont ajoutés au formulaire qui est lié à la <xref:System.Windows.Forms.BindingSource>. Ceci est, est tour lié à la `Customers` table dans le `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Le formulaire de test  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu jusqu'à ce point.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
1.  Sélectionnez**F5** pour exécuter l’application  
  
     Le formulaire s’affiche avec un <xref:System.Windows.Forms.DataGridView> contrôle sur ce dernier qui est rempli avec des données à partir de la `Customers` table.  
  
2.  Sur le **déboguer** menu, sélectionnez**arrêter le débogage**.  
  
## <a name="handleconcurrency-errors"></a>Erreurs de Handleconcurrency  
 Gestion des erreurs est varie selon les règles d’entreprise spécifiques qui régissent votre application. Pour cette procédure pas à pas, nous utilisons la stratégie suivante comme exemple de procédure tohandle l’erreur d’accès concurrentiel.  
  
 Les trois versions de l’enregistrement à l’utilisateur applicationpresents :  
  
- L’enregistrement actif dans la base de données  
  
- L’enregistrement d’origine qui est chargé dans le jeu de données  
  
- Les modifications proposées dans le jeu de données  
  
  L’utilisateur peut ensuite remplacer la base de données avec la version proposée, ou d’annuler la mise à jour et actualiser le jeu de données avec les nouvelles valeurs à partir de la base de données.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Pour activer la gestion des erreurs d’accès concurrentiel  
  
1.  Créer un gestionnaire d’erreurs personnalisé.  
  
2.  Afficher les choix à l’utilisateur.  
  
3.  Traiter la réponse de l’utilisateur.  
  
4.  Renvoyez la mise à jour ou réinitialiser les données dans le jeu de données.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode pour gérer l’exception d’accès concurrentiel  
 Lorsque vous tentez d’effectuer une mise à jour et une exception est générée, vous souhaitez généralement faire quelque chose avec les informations fournies par l’exception levée.  
  
 Dans cette section, vous ajoutez le code qui tente de mettre à jour de la base de données. Vous permet également de gérer les <xref:System.Data.DBConcurrencyException> susceptible d’être levée, ainsi que toute autre exception.  
  
> [!NOTE]
>  Le `CreateMessage` et `ProcessDialogResults` méthodes seront ajoutés plus loin dans cette procédure pas à pas.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Pour ajouter la gestion des erreurs pour l’erreur d’accès concurrentiel  
  
1.  Ajoutez le code suivant ci-dessous le `Form1_Load` méthode :  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  Remplacez le `CustomersBindingNavigatorSaveItem_Click` méthode à appeler le `UpdateDatabase` méthode afin qu’il ressemble à ce qui suit :  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices à l’utilisateur  
 Le code que vous venez de taper appelle le `CreateMessage` procédure pour afficher des informations d’erreur à l’utilisateur. Pour cette procédure pas à pas, vous utilisez une boîte de message pour afficher les différentes versions de l’enregistrement à l’utilisateur. Cela permet à l’utilisateur de choisir s’il faut remplacer l’enregistrement avec les modifications ou annuler la modification. Une fois que l’utilisateur sélectionne une option (clique sur un bouton) dans la boîte de message, la réponse est transmise à la `ProcessDialogResult` (méthode).  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Pour créer le message à afficher à l’utilisateur  
  
-   Créer le message en ajoutant le code suivant à la **éditeur de Code**. Entrez le code suivant sous le `UpdateDatabase` (méthode).  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Traiter la réponse de l’utilisateur  
 Vous devez également le code permettant de traiter la réponse de l’utilisateur à la boîte de message. Les options sont soit pour remplacer l’enregistrement actif dans la base de données par la modification proposée, ou abandonner les modifications locales et actualiser la table de données avec l’enregistrement qui se trouve actuellement dans la base de données. Si l’utilisateur clique sur Oui, le <xref:System.Data.DataTable.Merge%2A> méthode est appelée avec le *preserveChanges* affectée à l’argument `true`. Cela entraîne la tentative de mise à jour aboutisse, car la version d’origine de l’enregistrement correspond désormais à l’enregistrement dans la base de données.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Pour traiter l’utilisateur d’entrée à partir de la boîte de message  
  
-   Ajoutez le code suivant sous le code qui a été ajouté dans la section précédente.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Le formulaire de test  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu. Pour simuler une violation d’accès concurrentiel, vous devez modifier des données dans la base de données après avoir rempli le NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
1.  Sélectionnez**F5** pour exécuter l’application.  
  
2.  Une fois que le formulaire s’affiche, laissez-la en cours d’exécution et basculer vers l’IDE Visual Studio.  
  
3.  Sur le **vue** menu, choisissez **Explorateur de serveurs**.  
  
4.  Dans **Explorateur de serveurs**, développez la connexion de votre application est à l’aide, puis développez le **Tables** nœud.  
  
5.  Avec le bouton droit le **clients** table, puis sélectionnez **afficher les données de Table**.  
  
6.  Dans le premier enregistrement (`ALFKI`) modifier `ContactName` à `Maria Anders2`.  
  
    > [!NOTE]
    >  Accédez à une autre ligne pour valider la modification.  
  
7.  Basculez vers le `ConcurrencyWalkthrough`de l’exécution de formulaire.  
  
8.  Dans le premier enregistrement sur le formulaire (`ALFKI`), modifiez`ContactName` à `Maria Anders1`.  
  
9. Sélectionnez le **enregistrer** bouton.  
  
     L’erreur d’accès concurrentiel est levée, et la boîte de message s’affiche.  
  
10. En sélectionnant**non** annule la mise à jour et met à jour le jeu de données avec les valeurs qui se trouvent actuellement dans la base de données. En sélectionnant**Oui** écrit la valeur proposée dans la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)

