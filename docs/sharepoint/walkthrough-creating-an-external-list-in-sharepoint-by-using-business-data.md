---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une liste externe dans SharePoint &#224; l&#39;aide de donn&#233;es m&#233;tiers"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Business Data Connectivity (service) (développement SharePoint dans Visual Studio), données métiers dans un WebPart"
  - "BDC (développement SharePoint dans Visual Studio), liste externe"
  - "Business Data Connectivity (service) (développement SharePoint dans Visual Studio), données métiers dans une liste SharePoint"
  - "BDC (développement SharePoint dans Visual Studio), données métiers dans une liste SharePoint"
  - "BDC (développement SharePoint dans Visual Studio), données métiers dans un WebPart"
  - "BDC (développement SharePoint dans Visual Studio), liste stockée d’entités"
  - "Business Data Connectivity (service) (développement SharePoint dans Visual Studio), liste stockée d’entités"
  - "Business Data Connectivity (service) (développement SharePoint dans Visual Studio), liste externe"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une liste externe dans SharePoint &#224; l&#39;aide de donn&#233;es m&#233;tiers
  Le service de connectivité de données métiers \(BDC, Business Data Connectivity\) permet à SharePoint d'afficher des données métiers à partir d'applications de serveur principal, de services Web et de bases de données.  
  
 Cette procédure pas à pas vous indique comment créer un modèle de service BDC qui retourne des informations sur les contacts dans un exemple de base de données.  Elle vous indique ensuite comment créer une liste externe dans SharePoint à l'aide de ce modèle.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet  
  
-   Ajout d'une entité au modèle  
  
-   Ajout d'une méthode de recherche  
  
-   Ajout d'une méthode de recherche spécifique  
  
-   Test du projet.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] ou [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Accès à l'exemple de base de données AdventureWorks.  Pour plus d'informations sur l'installation de la base de données AdventureWorks, consultez [Exemples de bases de données SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483).  
  
## Création d'un projet qui contient un modèle BDC  
  
#### Pour créer un projet contenant un modèle BDC  
  
1.  Dans la barre de menus de Visual Studio, choisissez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint** puis choisissez l'élément **2010**.  
  
3.  Dans le volet **Modèles**, sélectionnez **SharePoint 2010 – Projet**, nomez le projet AdventureWorksTest, puis choisissez le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  En utilisant cet Assistant, vous pouvez sélectionner le site à utiliser pour déboguer le projet et définir le niveau de confiance de la solution.  
  
4.  Sélectionnez bouton d'option **Déployer en tant que solution de batterie** pour définir le niveau de confiance.  
  
5.  Cliquez sur le bouton **Terminer** pour accepter le site SharePoint local par défaut.  
  
6.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet SharePoint.  
  
7.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'ouvre.  
  
8.  Dans le volet de **Modèles**, choisissez **Modèle de connectivité de données métiers \(solution de batterie uniquement\)**, nommez le projet AdventureWorksContacts, puis cliquez sur le bouton **Ajouter**.  
  
## Ajout de classes d'accès aux données au projet  
  
#### Pour ajouter des classes d'accès aux données au projet  
  
1.  Dans le menu, choisissez **Outils**, **Se connecter à la base de données**.  
  
     La boîte de dialogue **Ajouter une connexion** s'ouvre.  
  
2.  Ajoutez une connexion à l'exemple de base de données SQL Server AdventureWorks.  
  
     Pour plus d'informations, consultez [Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/fr-fr/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  Dans l'**Explorateur de solutions**, choisissez le nœud du projet.  
  
4.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
5.  Dans le volet **Modèles installés**, choisissez le nœud **Données**.  
  
6.  Dans le volet **Modèles**, choisissez **Classes LINQ to SQL**.  
  
7.  Dans la zone de texte **Nom**, spécifiez AdventureWorks puis choisissez le bouton **Ajouter**.  
  
     Un fichier .dbml est ajouté au projet, et le Concepteur Objet\/Relationnel \(Concepteur O\/R\) s'ouvre.  
  
8.  Dans le menu, choisissez **Affichage**, **Explorateur de serveurs**.  
  
9. Dans l'**Explorateur de serveurs**, développez le nœud qui représente l'exemple de base de données AdventureWorks, puis développez le nœud **Tables**.  
  
10. Ajouter la table **Contact \(Personne\)** sur le Concepteur O\/R.  
  
     Une classe d'entité est créée et apparaît dans l'aire de conception.  La classe d'entité possède des propriétés qui correspondent aux colonnes dans la table Contact \(Personne\).  
  
## Suppression de l'entité par défaut du modèle BDC  
 Le projet **Modèle de connectivité de données métiers** ajoute une entité par défaut nommée Entity1 au modèle.  Supprimez cette entité.  Vous ajouterez une nouvelle entité par la suite.  Lorsque vous démarrez avec un modèle vide, le nombre d'étapes à suivre pour exécuter la procédure pas à pas diminue.  
  
#### Pour supprimer l'entité par défaut du modèle  
  
1.  Dans l'**Explorateur de solutions**, développez le nœud **BdcModel1**, puis ouvrez le fichier BdcModel1.bdcm.  
  
2.  Le fichier de modèle de connectivité de donnés métiers s'ouvre dans le concepteur BDC.  
  
3.  Dans le Concepteur, ouvrez le menu contextuel du nœud **Entity1**, puis choisissez **Supprimer**.  
  
4.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour Entity1.vb \(en Visual Basic\) ou \(Entity1.cs en c\), puis choisissez **Supprimer**.  
  
5.  Ouvrir le menu contextuel pour Entity1Service.vb \(en Visual Basic\) ou \(Entity1Service.cs en c\), puis choisissez **Supprimer**.  
  
## Ajout d'une entité au modèle  
 Pour ajouter une entité au modèle,  vous pouvez ajouter des entités de la **Boîte à outils** de Visual Studio sur le concepteur BDC.  
  
#### Pour ajouter une entité au modèle  
  
1.  Dans la barre de menus, choisissez **Affichage**, **Boîte à outils**.  
  
2.  Sur l'onglet **BusinessDataConnectivity** de la **Boîte à outils**, ajouter une **Entité** sur le concepteur BDC.  
  
     La nouvelle entité s'affiche dans le concepteur.  Visual Studio ajoute un fichier nommé EntityService.vb \(en Visual Basic\) ou EntityService.cs \(en C\#\) au projet.  
  
3.  Dans la barre de menus, choisissez **Affichage**, **Propriétés**, **Fenêtre**.  
  
4.  Dans la fenêtre **Propriétés**, affectez à la valeur de propriété **Name** à Contact.  
  
5.  Dans le Concepteur, ouvrez le menu contextuel de l'entité, choisissez **ajouter**, puis choisissez **Identificateur**.  
  
     Un nouvel identificateur s'affiche sur l'entité.  
  
6.  Dans la fenêtre **Propriétés**, renommez l'identificateur en ContactID.  
  
7.  Dans la liste **Nom de type**, choisissez **System.Int32**.  
  
## Ajout d'une méthode de recherche spécifique  
 Pour que le service BDC puisse afficher un contact spécifique, vous devez ajouter une méthode de recherche spécifique.  Le service BDC appelle la méthode de recherche spécifique lorsqu'un utilisateur choisit un élément dans une liste et choisit ensuite le bouton **Afficher l'élément** sur le ruban.  
  
 Vous pouvez ajouter une méthode de recherche spécifique à l'entité Contact à partir de la fenêtre **Détails de méthode BDC**.  Pour retourner une entité spécifique, ajoutez du code à la méthode.  
  
#### Pour ajouter une méthode de recherche spécifique  
  
1.  Dans le concepteur BDC, choisissez l'entité **Contact**.  
  
2.  Dans la barre de menus, cliquez sur **Affichage**, **Autres fenêtres**, **Détails de la méthode BDC**.  
  
     La fenêtre Détails de méthode BDC s'ouvre.  
  
3.  Dans la liste **Ajouter une méthode**, choisissez **Créer une méthode de recherche spécifique**.  
  
     Visual Studio ajoute les éléments suivants au modèle.  Ces éléments apparaissent dans la fenêtre **Détails de méthode BDC**.  
  
    -   Méthode nommée ReadItem  
  
    -   Paramètre d'entrée pour la méthode  
  
    -   Paramètre de retour pour la méthode  
  
    -   Descripteur de type pour chaque paramètre  
  
    -   Instance de méthode pour la méthode  
  
4.  Dans la fenêtre **Détails de méthode BDC**, ouvrez sur la liste déroulante correspondant au descripteur de type **Contact**, puis choisissez **Modifier**.  
  
     L'**Explorateur BDC** ouvre et propose une vue hiérarchique du modèle.  
  
5.  Dans la fenêtre **Propriétés**, ouvrez la liste à côté de la propriété **TypeName**, choisissez l'onglet **Projet actuel**, puis sélectionnez la propriété **Contact**.  
  
6.  Dans l'**Explorateur BDC**, ouvrez le menu contextuel du **Contact**, puis choisissez **Ajouter un descripteur de type**.  
  
     Un nouveau descripteur de type qui est nommé **TypeDescriptor1** s'affiche dans l'**Explorateur BDC**.  
  
7.  Dans la fenêtre **Propriétés**, affectez la valeur de la propriété **Name** à **ContactID**.  
  
8.  Ouvrez la liste à côté de la propriété **TypeName**, puis choisissez **Int32**.  
  
9. Ouvrez la liste à côté de la propriété **Identificateur**, puis choisissez **ContactID**.  
  
10. Répétez l'étape 6 pour créer un descripteur de type pour chacun des champs suivants.  
  
    |Nom|Nom de type|  
    |---------|-----------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Phone|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. Dans le concepteur BDC, sur l'entité **Contact**, ouvrez la méthode **ReadItem**.  
  
     Le fichier de code de service Contact s'ouvre dans l'éditeur de code.  
  
12. Dans la classe `ContactService`, remplacez la méthode `ReadItem` par le code suivant.  Ce code exécute les tâches suivantes :  
  
    -   Il récupère un enregistrement à partir de la table Contact de la base de données AdventureWorks.  
  
    -   Il retourne une entité Contact au service BDC.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Ajout d'une méthode de recherche  
 Pour que le service BDC puisse afficher les contacts dans une liste, vous devez ajouter une méthode de recherche.  Ajoutez une méthode de recherche à l'entité Contact à partir de la fenêtre **Détails de méthode BDC**.  Pour retourner une collection d'entités au service BDC, ajoutez du code à la méthode.  
  
#### Pour ajouter une méthode de recherche  
  
1.  Dans le concepteur BDC, choisissez l'entité **Contact**.  
  
2.  Dans la fenêtre **Détails de méthode BDC**, réduisez le nœud **ReadItem**.  
  
3.  Dans la liste **Ajouter une méthode** sous la méthode **ReadList**, choisissez **Créer une méthode de recherche**.  
  
     Visual Studio ajoute une méthode, un paramètre de retour et un descripteur de type.  
  
4.  Dans le concepteur BDC, sur l'entité **Contact**, ouvrez la méthode **ReadList**.  
  
     Le fichier de code pour le service Contact s'ouvre dans l'éditeur de code.  
  
5.  Dans la classe `ContactService`, remplacez la méthode `ReadList` par le code suivant.  Ce code exécute les tâches suivantes :  
  
    -   Il récupère des données à partir de la table Contacts de la base de données AdventureWorks.  
  
    -   Il retourne une liste d'entités Contact au service BDC.  
  
    > [!NOTE]  
    >  Remplacez la valeur du champ `ServerName` par le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Test du projet  
 Lorsque vous exécutez le projet, le site SharePoint s'ouvre et Visual Studio ajoute votre modèle au service de connectivité de données métiers.  Vous pouvez créer dans SharePoint une liste externe qui référence l'entité Contact.  Les données des contacts figurant dans la base de données AdventureWorks s'affichent dans la liste.  
  
> [!NOTE]  
>  Vous devrez peut\-être modifier vos paramètres de sécurité dans SharePoint avant de pouvoir déboguer votre solution.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### Pour tester le projet  
  
1.  Appuyez sur la touche **F5**.  
  
     Le site SharePoint s'ouvre.  
  
2.  Dans le menu **Actions de site**, choisissez la commande **Autres options**.  
  
3.  Dans la page **Créer**, sélectionnez le modèle **Liste externe**, puis cliquez sur le bouton **Créer**.  
  
4.  Nommez la liste personnalisée Contacts.  
  
5.  Choisissez le bouton Parcourir en regard du champ **Type de contenu externe**.  
  
6.  Dans la boîte de dialogue **Sélecteur de types de contenu externe**, choisissez l'élément **AdventureWorksContacts.BdcModel1.Contact**, puis choisissez le bouton **Créer**.  
  
     SharePoint crée une liste externe qui contient des contacts de l'exemple de base de données AdventureWorks.  
  
7.  Pour tester la méthode de recherche spécifique, choisissez un contact dans la liste.  
  
8.  Sur le Ruban, cliquez sur l'onglet **Éléments**, puis sélectionnez la commande **Afficher l'élément**.  
  
     Les détails du contact que vous avez choisi s'affichent sur un formulaire.  
  
## Étapes suivantes  
 Pour savoir comment concevoir des modèles pour le service BDC dans SharePoint, consultez les rubriques suivantes :  
  
-   [Comment : ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md).  
  
## Voir aussi  
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  