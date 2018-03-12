---
title: "Procédure pas à pas : Création d’une Page d’Application SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 33c718707ce284179b69e33677d5b29f0d4433c7
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>Procédure pas à pas : création d'une page d'application SharePoint
 
Une page d’application est un type spécial d’une page ASP.NET. Pages d’application présentent du contenu qui est fusionné avec une page maître SharePoint. Pour plus d’informations, consultez [création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Cette procédure pas à pas montre comment créer une page d’application et puis de le déboguer à l’aide d’un site SharePoint local. Cette page affiche tous les éléments de chaque utilisateur a créé ou modifié dans tous les sites de la batterie de serveurs.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet SharePoint.
- Ajout d’une page d’application au projet SharePoint.
- Ajout de contrôles ASP.NET à la page de l’application.
- Ajout d’un code derrière les contrôles ASP.NET.
- Test de la page d’application.

> [!NOTE]
> Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

- Éditions prises en charge de Windows et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

## <a name="creating-a-sharepoint-project"></a>Création d'un projet SharePoint

Commencez par créer un **projet SharePoint vide**. Une version ultérieure, vous ajouterez un **Page Application** élément à ce projet.

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Ouvrez le **nouveau projet** boîte de dialogue, développez le **Office/SharePoint** nœud sous le langage que vous souhaitez utiliser, puis choisissez le **Solutions SharePoint** nœud.

3. Dans le **modèles Visual Studio installés** volet, choisissez la **SharePoint 2010 - projet vide** modèle. Nommez le projet **MySharePointProject**, puis choisissez le **OK** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche. Cet Assistant vous permet de sélectionner le site que vous allez utiliser pour déboguer le projet et le niveau de confiance de la solution.

4. Choisissez le **déployer une solution de batterie de serveurs** case d’option, puis choisissez le **Terminer** bouton pour accepter le site SharePoint local par défaut.

## <a name="creating-an-application-page"></a>Création d’une Page d’Application

Pour créer une page d’application, ajoutez un **Page Application** élément au projet.

1. Dans **l’Explorateur de solutions**, choisissez le **MySharePointProject** projet.

2. Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.

3. Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **Page d’Application (Solution de batterie uniquement** modèle.

4. Nommez la page **SearchItems**, puis choisissez le **ajouter** bouton.

     Le concepteur Visual Web Developer affiche la page d’application dans **Source** où vous pouvez consulter les éléments HTML de la page de vue. Le concepteur affiche le balisage pour plusieurs <xref:System.Web.UI.WebControls.Content> contrôles. Chaque contrôle est mappé à un <xref:System.Web.UI.WebControls.ContentPlaceHolder> contrôle qui est défini dans la page maître d’application par défaut.

## <a name="designing-the-layout-of-the-application-page"></a>Définition de la disposition de la Page d’Application

L’élément de Page de l’Application vous permet d’utiliser un concepteur pour ajouter des contrôles ASP.NET à la page de l’application. Ce concepteur est le même utilisé dans Visual Web Developer. Ajouter une étiquette, une liste de cases d’option et une table pour le **Source** afficher du concepteur, puis définissez les propriétés comme vous le feriez lorsque vous concevez une page ASP.NET standard.

1. Dans la barre de menus, choisissez **Affichage**, **Boîte à outils**.

2. Dans le nœud Standard de la **boîte à outils**, effectuez l’une des étapes suivantes :

    - Ouvrez le menu contextuel pour le **étiquette** d’élément, choisissez **copie**, ouvrez le menu contextuel de la ligne dans le **PlaceHolderMain** contrôle dans le concepteur, de contenu, puis Choisissez **coller**.

    - Faites glisser le **étiquette** d’élément du **boîte à outils** sur le corps de la **PlaceHolderMain** contrôle de contenu.

3. Répétez l’étape précédente pour ajouter un **DropDownList** élément et un **Table** d’élément à la **PlaceHolderMain** contrôle de contenu.

4. Dans le concepteur, modifiez la valeur de la `Text` attribut du contrôle label pour **afficher tous les éléments**.

5. Dans le concepteur, remplacez le `<asp:DropDownList>` élément avec le code XML suivant.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handling-the-events-of-controls-on-the-page"></a>La gestion des événements de contrôles sur la Page

Gérer les contrôles dans une page d’application comme vous le feriez pour n’importe quelle page ASP.NET. Dans cette procédure, vous allez gérer le `SelectedIndexChanged` l’événement de la liste déroulante.

1. Sur le **vue** menu, choisissez **Code**.

     Le fichier de code de page application s’ouvre dans l’éditeur de Code.

2. Ajoutez la méthode suivante à la classe `SearchItems`. Ce code gère le <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> l’événement de la <xref:System.Web.UI.WebControls.DropDownList> en appelant une méthode que vous créerez plus loin dans cette procédure pas à pas.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Ajoutez les instructions suivantes en haut du fichier de code page application.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Ajoutez la méthode suivante à la classe `SearchItems`. Cette méthode effectue une itération dans tous les sites de la batterie de serveurs et recherche les éléments créés ou modifiés par l’utilisateur actuel.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Ajoutez la méthode suivante à la classe `SearchItems`. Cette méthode affiche les éléments créés ou modifiés par l’utilisateur actuel dans la table.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="testing-the-application-page"></a>Test de la Page d’Application

Lorsque vous exécutez le projet, le site SharePoint s’ouvre et la page d’application s’affiche.

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel de la page d’application, puis choisissez **définir comme élément de démarrage**.

2. Appuyez sur la touche F5.

     Le site SharePoint s’ouvre.

3. Dans la page application, choisissez le **modifiés par moi** option.

     La page d’application actualise et affiche tous les éléments que vous avez modifié dans tous les sites de la batterie de serveurs.

4. Dans la page application, choisissez **créés par moi** dans la liste.

     La page d’application actualise et affiche tous les éléments que vous avez créé dans tous les sites de la batterie de serveurs.

## <a name="next-ateps"></a>Ateps suivant

Pour plus d’informations sur les pages d’application SharePoint, consultez [création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Vous pouvez en savoir plus sur la conception de contenu de la page SharePoint à l’aide du Concepteur Web visuel à partir de ces rubriques :

- [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer une page d’application](../sharepoint/how-to-create-an-application-page.md)  
[Page application _layouts, tapez](http://go.microsoft.com/fwlink/?LinkID=169274)
