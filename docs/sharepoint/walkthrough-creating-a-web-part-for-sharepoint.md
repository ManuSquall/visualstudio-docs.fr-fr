---
title: 'Procédure pas à pas : création d’un composant WebPart pour SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d8b5e05fb234e9997bce615f7b2de1d790c1ae0
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014576"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Procédure pas à pas : créer un composant WebPart pour SharePoint

Composants WebPart permettre aux utilisateurs de modifier directement le contenu, l’apparence et le comportement des pages de site SharePoint à l’aide d’un navigateur. Cette procédure pas à pas vous montre comment créer un composant WebPart à l’aide du modèle d’élément **WebPart** dans Visual Studio 2010.

Le composant WebPart affiche les employés dans une grille de données. L’utilisateur spécifie l’emplacement du fichier qui contient les données de l’employé. L’utilisateur peut également filtrer la grille de données afin que les employés qui sont des responsables apparaissent dans la liste uniquement.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un composant WebPart à l’aide du modèle d’élément de **composant WebPart** Visual Studio.

- Création d’une propriété qui peut être définie par l’utilisateur du composant WebPart. Cette propriété spécifie l’emplacement du fichier de données de l’employé.

- Rendu du contenu dans un composant WebPart en ajoutant des contrôles à la collection de contrôles WebPart.

- Création d’un nouvel élément de menu, appelé *verbe,* qui apparaît dans le menu d’actions verbales du composant WebPart rendu. Les verbes permettent à l’utilisateur de modifier les données qui s’affichent dans le composant WebPart.

- Test du composant WebPart dans SharePoint.

    > [!NOTE]
    > Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

- Éditions prises en charge de Microsoft Windows et SharePoint.

- Visual Studio 2017 ou Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Créer un projet SharePoint vide

Commencez par créer un projet SharePoint vide. Plus tard, vous allez ajouter un composant WebPart au projet à l’aide du modèle d’élément **WebPart** .

1. Commencez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] par utiliser l’option **exécuter en tant qu’administrateur** .

2. Dans la barre hommes, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. Dans la boîte de dialogue **nouveau projet** , développez le nœud **SharePoint** sous la langue que vous souhaitez utiliser, puis choisissez le nœud **2010** .

4. Dans le volet **modèles** , choisissez **projet SharePoint 2010**, puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche. Cet Assistant vous permet de sélectionner le site que vous allez utiliser pour déboguer le projet et le niveau de confiance de la solution.

5. Sélectionnez la case d’option **déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** pour accepter le site SharePoint local par défaut.

## <a name="add-a-web-part-to-the-project"></a>Ajouter un composant WebPart au projet

Ajoutez un élément **WebPart** au projet. L’élément **WebPart** ajoute le fichier de code du composant WebPart. Plus tard, vous ajouterez du code au fichier de code du composant WebPart pour afficher le contenu du composant WebPart.

1. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet **modèles installés** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

3. Dans la liste des modèles SharePoint, choisissez le modèle **WebPart** , puis cliquez sur le bouton **Ajouter** .

     L’élément **WebPart** s’affiche dans **Explorateur de solutions**.

## <a name="rendering-content-in-the-web-part"></a>Rendu du contenu dans le composant WebPart

Vous pouvez spécifier les contrôles que vous souhaitez voir apparaître dans le composant WebPart en les ajoutant à la collection Controls de la classe WebPart.

1. Dans **Explorateur de solutions**, ouvrez *WebPart1. vb* (dans Visual Basic) ou *WebPart1.cs* (en C#).

     Le fichier de code du composant WebPart s’ouvre dans l’éditeur de code.

2. Ajoutez les directives suivantes en haut du fichier de code du composant WebPart.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Ajoutez le code suivant à la classe `WebPart1` . Ce code déclare les champs suivants :

   - Une grille de données pour afficher les employés dans le composant WebPart.

   - Texte qui apparaît sur le contrôle utilisé pour filtrer la grille de données.

   - Étiquette qui affiche une erreur si la grille de données ne peut pas afficher les données.

   - Chaîne qui contient le chemin d’accès du fichier de données de l’employé.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Ajoutez le code suivant à la classe `WebPart1` . Ce code ajoute une propriété personnalisée nommée `DataFilePath` au composant WebPart. Une propriété personnalisée est une propriété qui peut être définie dans SharePoint par l’utilisateur. Cette propriété obtient et définit l’emplacement d’un fichier de données XML utilisé pour remplir la grille de données.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Remplacez la méthode `CreateChildControls` par le code suivant. Ce code effectue les tâches suivantes :

   - Ajoute la grille de données et l’étiquette que vous avez déclarée à l’étape précédente.

   - Lie la grille de données à un fichier XML qui contient les données des employés.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Ajoutez la méthode suivante à la classe `WebPart1`. Ce code effectue les tâches suivantes :

   - Crée un verbe qui apparaît dans le menu d’actions verbales du composant WebPart rendu.

   - Il gère l'événement qui est déclenché lorsque l'utilisateur sélectionne le verbe dans le menu d'actions verbales. Ce code filtre la liste des employés qui s’affichent dans la grille de données.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Tester le composant WebPart

Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Le composant WebPart est automatiquement ajouté à la Galerie de composants WebPart dans SharePoint. Vous pouvez ajouter le composant WebPart à n’importe quelle page de composant WebPart.

1. Collez le code XML suivant dans un fichier bloc-notes. Ce fichier XML contient les exemples de données qui s’affichent dans le composant WebPart.

    ```xml
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

2. Dans le bloc-notes, dans la barre de menus, choisissez **fichier**  >  **Enregistrer sous**.

3. Dans la boîte de dialogue **Enregistrer sous** , dans la liste **type** de fichier, choisissez **tous les fichiers**.

4. Dans la zone **nom de fichier** , entrez **data.xml**.

5. Choisissez un dossier à l’aide du bouton **Parcourir les dossiers** , puis cliquez sur le bouton **Enregistrer** .

6. Dans Visual Studio, appuyez sur la touche **F5** .

     Le site SharePoint s’ouvre.

7. Dans le menu **actions du site** , choisissez plus d' **options**.

8. Dans la page **créer** , choisissez le type de **page de composant WebPart** , puis cliquez sur le bouton **créer** .

9. Dans la page **nouvelle page de composant WebPart** , nommez la page **SampleWebPartPage. aspx**, puis choisissez le bouton **créer** .

     La page du composant WebPart s’affiche.

10. Sélectionnez une zone dans la page du composant WebPart.

11. En haut de la page, choisissez l’onglet **Insérer** , puis cliquez sur le bouton **composant WebPart** .

12. Dans le volet **catégories** , choisissez le dossier **personnalisé** , choisissez le composant WebPart **WebPart1** , puis cliquez sur le bouton **Ajouter** .

     Le composant WebPart s’affiche sur la page.

## <a name="test-the-custom-property"></a>Tester la propriété personnalisée

Pour remplir la grille de données qui s’affiche dans le composant WebPart, spécifiez le chemin d’accès du fichier XML qui contient les données relatives à chaque employé.

1. Choisissez la flèche qui apparaît sur le côté droit du composant WebPart, puis choisissez **modifier le composant WebPart** dans le menu qui s’affiche.

     Un volet qui contient les propriétés du composant WebPart s’affiche sur le côté droit de la page.

2. Dans le volet, développez le nœud **divers** , entrez le chemin d’accès du fichier XML que vous avez créé précédemment, choisissez le bouton **appliquer** , puis cliquez sur le bouton **OK** .

     Vérifiez qu’une liste d’employés s’affiche dans le composant WebPart.

## <a name="test-the-web-part-verb"></a>Tester le verbe du composant WebPart

Affichez et masquez les employés qui ne sont pas responsables en cliquant sur un élément qui s’affiche dans le menu d’actions verbales du composant WebPart.

1. Choisissez la flèche qui apparaît sur le côté droit du composant WebPart, puis choisissez **afficher les gestionnaires uniquement** dans le menu qui s’affiche.

     Seuls les employés qui sont des responsables apparaissent dans le composant WebPart.

2. Cliquez à nouveau sur la flèche, puis choisissez **Afficher tous les employés** dans le menu qui s’affiche.

     Tous les employés s’affichent dans le composant WebPart.

## <a name="see-also"></a>Voir aussi

[Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Procédure pas à pas : créer un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
