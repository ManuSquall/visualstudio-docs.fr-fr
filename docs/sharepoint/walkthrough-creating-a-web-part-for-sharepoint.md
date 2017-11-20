---
title: "Procédure pas à pas : Création d’un composant WebPart pour SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3293382ffc0c36fb78bb115d0f38c311278a7151
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint"></a>Procédure pas à pas : création d'un composant WebPart pour SharePoint
  WebPart permettent aux utilisateurs de modifier directement le contenu, l’apparence et le comportement des pages du site SharePoint à l’aide d’un navigateur. Cette procédure pas à pas vous montre comment créer un composant WebPart à l’aide de la **WebPart** modèle d’élément dans Visual Studio 2010.  
  
 Le composant WebPart affiche les employés dans une grille de données. L’utilisateur spécifie l’emplacement du fichier qui contient les données d’employé. L’utilisateur peut également filtrer la grille de données afin que les employés qui sont responsables s’affichent dans la liste uniquement.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un composant WebPart à l’aide de Visual Studio **WebPart** modèle d’élément.  
  
-   Création d’une propriété qui peut être définie par l’utilisateur du composant WebPart. Cette propriété spécifie l’emplacement du fichier de données employé.  
  
-   Collection de contrôles contenus dans un composant WebPart de rendu en ajoutant des contrôles au composant WebPart.  
  
-   Création d’un nouvel élément de menu, désigné par un *verbe,* qui apparaît dans le menu d’actions verbales du composant WebPart restitué. Verbes permettent à l’utilisateur de modifier les données qui s’affiche dans le composant WebPart.  
  
-   Tester le composant WebPart dans SharePoint.  
  
    > [!NOTE]  
    >  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Microsoft Windows et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]ou une édition de Visual Studio Application Lifecycle Management (ALM).  
  
## <a name="creating-an-empty-sharepoint-project"></a>Créez un projet SharePoint vide  
 Commencez par créer un projet SharePoint vide. Une version ultérieure, vous allez ajouter un composant WebPart au projet à l’aide de la **WebPart** modèle d’élément.  
  
#### <a name="to-create-an-empty-sharepoint-project"></a>Pour créer un projet SharePoint vide  
  
1.  Démarrer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à l’aide de la **exécuter en tant qu’administrateur** option.  
  
2.  Dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud sous le langage que vous souhaitez utiliser, puis choisissez le **2010** nœud.  
  
4.  Dans le **modèles** volet, choisissez **projet SharePoint 2010**, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche. Cet Assistant vous permet de sélectionner le site que vous allez utiliser pour déboguer le projet et le niveau de confiance de la solution.  
  
5.  Choisissez le **déployer une solution de batterie de serveurs** case d’option, puis choisissez le **Terminer** bouton pour accepter le site SharePoint local par défaut.  
  
## <a name="adding-a-web-part-to-the-project"></a>Ajout d’un composant WebPart au projet  
 Ajouter un **WebPart** élément au projet. Le **WebPart** élément ajoute le fichier de code du composant WebPart. Une version ultérieure, vous ajouterez le code au fichier de code pour restituer le contenu du composant WebPart.  
  
#### <a name="to-add-a-web-part-to-the-project"></a>Pour ajouter un composant WebPart au projet  
  
1.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles installés** volet, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
3.  Dans la liste de modèles SharePoint, choisissez le **WebPart** modèle, puis choisissez le **ajouter** bouton.  
  
     Le **WebPart** élément apparaît dans **l’Explorateur de solutions**.  
  
## <a name="rendering-content-in-the-web-part"></a>Rendu de contenu dans le composant WebPart  
 Vous pouvez spécifier les contrôles que vous souhaitez voir apparaître dans le composant WebPart en les ajoutant à la collection de contrôles de la classe de composant WebPart.  
  
#### <a name="to-render-content-in-the-web-part"></a>Pour afficher le contenu dans le composant WebPart  
  
1.  Dans **l’Explorateur de solutions**, ouvrez WebPart1.vb (en Visual Basic) ou WebPart1.cs (en c#).  
  
     Le fichier de code du composant WebPart s’ouvre dans l’éditeur de Code.  
  
2.  Ajoutez les instructions suivantes en haut du fichier de code de composant WebPart.  
  
     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]  
  
3.  Ajoutez le code suivant à la classe `WebPart1`. Ce code déclare les champs suivants :  
  
    -   Une grille de données pour afficher les employés dans le composant WebPart.  
  
    -   Texte qui apparaît sur le contrôle qui est utilisé pour filtrer la grille de données.  
  
    -   Une étiquette qui affiche une erreur si la grille de données est impossible d’afficher les données.  
  
    -   Chaîne qui contient le chemin d’accès du fichier de données employé.  
  
     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]  
  
4.  Ajoutez le code suivant à la classe `WebPart1`. Ce code ajoute une propriété personnalisée nommée `DataFilePath` au composant WebPart. Une propriété personnalisée est une propriété qui peut être définie par l’utilisateur dans SharePoint. Cette propriété obtient et définit l’emplacement d’un fichier de données XML qui est utilisé pour remplir la grille de données.  
  
     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]  
  
5.  Remplacez la méthode `CreateChildControls` par le code suivant. Ce code exécute les tâches suivantes :  
  
    -   Ajoute la grille de données et l’étiquette que vous avez déclaré à l’étape précédente.  
  
    -   Lie la grille de données dans un fichier XML qui contient les données de l’employé.  
  
     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]  
  
6.  Ajoutez la méthode suivante à la classe `WebPart1`. Ce code exécute les tâches suivantes :  
  
    -   Crée un verbe qui apparaît dans le menu de verbes WebPart du composant WebPart restitué.  
  
    -   Il gère l'événement qui est déclenché lorsque l'utilisateur sélectionne le verbe dans le menu d'actions verbales. Ce code filtre la liste des employés qui s’affiche dans la grille de données.  
  
     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]  
  
## <a name="testing-the-web-part"></a>Le composant WebPart de test  
 Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Le composant WebPart est automatiquement ajouté à la galerie de composants WebPart dans SharePoint. Vous pouvez ajouter le composant WebPart à une page WebPart.  
  
#### <a name="to-test-the-web-part"></a>Pour tester le composant WebPart  
  
1.  Collez le code XML suivant dans un fichier du bloc-notes. Ce fichier XML contient les exemples de données qui apparaîtra dans le composant WebPart.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
           <employee>  
               <name>David Hamilton</name>  
               <hireDate>2001-05-11</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
           <employee>  
               <name>Karina Leal</name>  
               <hireDate>1999-04-01</hireDate>  
               <title>Manager</title>  
           </employee>  
           <employee>  
               <name>Nancy Davolio</name>  
               <hireDate>1992-05-01</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
           <employee>  
               <name>Steven Buchanan</name>  
               <hireDate>1955-03-04</hireDate>  
               <title>Manager</title>  
           </employee>  
           <employee>  
               <name>Suyama Michael</name>  
               <hireDate>1963-07-02</hireDate>  
               <title>Sales Associate</title>  
           </employee>  
        </employees>  
    ```  
  
2.  Dans le bloc-notes, dans la barre de menus, choisissez **fichier**, **Enregistrer sous**.  
  
3.  Dans le **enregistrer en tant que** boîte de dialogue le **enregistrer en tant que type** , choisissez **tous les fichiers**.  
  
4.  Dans le **nom de fichier** , entrez **data.xml**.  
  
5.  Sélectionnez un dossier à l’aide de la **parcourir les dossiers** bouton, puis choisissez le **enregistrer** bouton.  
  
6.  Dans Visual Studio, choisissez le **F5** clé.  
  
     Le site SharePoint s’ouvre.  
  
7.  Sur le **Actions du Site** menu, choisissez **plus d’Options**.  
  
8.  Dans le **créer** page, choisissez la **Page WebPart** tapez, puis choisissez le **créer** bouton.  
  
9. Dans le **nouvelle Page WebPart** page, nommez la page **SampleWebPartPage.aspx**, puis choisissez le **créer** bouton.  
  
     La page de composant WebPart s’affiche.  
  
10. Sélectionnez une zone sur la page de composant WebPart.  
  
11. En haut de la page, choisissez la **insérer** onglet, puis choisissez le **WebPart** bouton.  
  
12. Dans le **catégories** volet, choisissez la **personnalisé** dossier, choisissez le **WebPart1** WebPart, puis choisissez le **ajouter** bouton.  
  
     Le composant WebPart apparaît sur la page.  
  
## <a name="testing-the-custom-property"></a>Test de la propriété personnalisée  
 Pour remplir la grille de données qui s’affiche dans le composant WebPart, spécifiez le chemin d’accès du fichier XML qui contient les données relatives à chaque employé.  
  
#### <a name="to-test-the-custom-property"></a>Pour tester la propriété personnalisée  
  
1.  Choisissez la flèche qui apparaît sur le côté droit du composant WebPart, puis **modifier des composants WebPart** dans le menu qui s’affiche.  
  
     Un volet qui contient les propriétés pour le composant WebPart apparaît sur le côté droit de la page.  
  
2.  Dans le volet, développez le **divers** nœud, entrez le chemin d’accès du fichier XML que vous avez créé précédemment, choisissez le **appliquer** bouton, puis choisissez le **OK** bouton.  
  
     Vérifiez qu’une liste d’employés s’affiche dans le composant WebPart.  
  
## <a name="testing-the-web-part-verb"></a>Test du verbe WebPart  
 Afficher et masquer les employés qui ne sont pas responsables en cliquant sur un élément qui apparaît dans le menu de verbes WebPart.  
  
#### <a name="to-test-the-web-part-verb"></a>Pour tester le verbe WebPart  
  
1.  Choisissez la flèche qui apparaît sur le côté droit du composant WebPart, puis **afficher uniquement les directeurs** dans le menu qui s’affiche.  
  
     Seuls les employés qui sont responsables s’affichent dans le composant WebPart.  
  
2.  Cliquez à nouveau sur la flèche, puis choisissez **afficher tous les employés** dans le menu qui s’affiche.  
  
     Tous les employés s’affichent dans le composant WebPart.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procédure pas à pas : création d’un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  