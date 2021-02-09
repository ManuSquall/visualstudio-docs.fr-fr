---
title: 'Procédure pas à pas : création d’une page d’application SharePoint | Microsoft Docs'
description: Dans cette procédure pas à pas, créez une page d’application (forme spécialisée d’une page ASP.NET), puis déboguez-la à l’aide d’un site SharePoint local.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: def9407d309e5f673d0a7a2cdc3710fae557be50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847841"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Procédure pas à pas : créer une page d’application SharePoint

Une page d’application est une forme spécialisée d’une page ASP.NET. Les pages d’application contiennent du contenu qui est fusionné avec une page maître SharePoint. Pour plus d’informations, consultez [créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Cette procédure pas à pas vous montre comment créer une page d’application et la déboguer à l’aide d’un site SharePoint local. Cette page affiche tous les éléments créés ou modifiés par chaque utilisateur dans tous les sites de la batterie de serveurs.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet SharePoint.
- Ajout d’une page d’application au projet SharePoint.
- Ajout de contrôles ASP.NET à la page d’application.
- Ajout de code-behind des contrôles ASP.NET.
- Test de la page de l’application.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

- Éditions prises en charge de Windows et SharePoint.

## <a name="create-a-sharepoint-project"></a>Créer un projet SharePoint

Commencez par créer un **projet SharePoint vide**. Plus tard, vous ajouterez un élément de **page d’application** à ce projet.

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Ouvrez la boîte de dialogue **nouveau projet** , développez le nœud **Office/SharePoint** sous la langue que vous souhaitez utiliser, puis choisissez le nœud **solutions SharePoint** .

3. Dans le volet **modèles Visual Studio installés** , choisissez le modèle de **projet SharePoint 2010-vide** . Nommez le projet **MySharePointProject**, puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche. Cet Assistant vous permet de sélectionner le site que vous allez utiliser pour déboguer le projet et le niveau de confiance de la solution.

4. Sélectionnez la case d’option **déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** pour accepter le site SharePoint local par défaut.

## <a name="create-an-application-page"></a>Page créer une application

Pour créer une page d’application, ajoutez un élément de **page d’application** au projet.

1. Dans **Explorateur de solutions**, choisissez le projet **MySharePointProject** .

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le modèle **page application (solution de batterie uniquement** ).

4. Nommez la page **SearchItems**, puis cliquez sur le bouton **Ajouter** .

     Le concepteur Visual Web Developer affiche la page application en mode **source** dans laquelle vous pouvez voir les éléments HTML de la page. Le concepteur affiche le balisage pour plusieurs <xref:System.Web.UI.WebControls.Content> contrôles. Chaque contrôle est mappé à un <xref:System.Web.UI.WebControls.ContentPlaceHolder> contrôle défini dans la page maître d’application par défaut.

## <a name="design-the-layout-of-the-application-page"></a>Concevoir la disposition de la page d’application

L’élément de page application vous permet d’utiliser un concepteur pour ajouter des contrôles ASP.NET à la page d’application. Ce concepteur est le même que celui utilisé dans Visual Web Developer. Ajoutez une étiquette, une liste de cases d’option et une table à la vue **source** du concepteur, puis définissez les propriétés comme vous le feriez lors de la conception d’une page ASP.NET standard.

1. Dans la barre de menus, choisissez **Afficher** la  >  **boîte à outils**.

2. Dans le nœud standard de la **boîte à outils**, effectuez l’une des opérations suivantes :

    - Ouvrez le menu contextuel de l’élément d' **étiquette** , choisissez **copier**, ouvrez le menu contextuel de la ligne sous le contrôle de contenu **PlaceHolderMain** dans le concepteur, puis choisissez **coller**.

    - Faites glisser l’élément **label** de la **boîte à outils** vers le corps du contrôle de contenu **PlaceHolderMain** .

3. Répétez l’étape précédente pour ajouter un élément **DropDownList** et un élément de **table** au contrôle de contenu **PlaceHolderMain** .

4. Dans le concepteur, modifiez la valeur de l' `Text` attribut du contrôle Label pour **Afficher tous les éléments**.

5. Dans le concepteur, remplacez l' `<asp:DropDownList>` élément par le code XML suivant.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Gérer les événements de contrôles sur la page

Gérez les contrôles dans une page d’application comme vous le feriez pour n’importe quelle page ASP.NET. Dans cette procédure, vous allez gérer l' `SelectedIndexChanged` événement de la liste déroulante.

1. Dans le menu **affichage** , choisissez **code**.

     Le fichier de code de la page d’application s’ouvre dans l’éditeur de code.

2. Ajoutez la méthode suivante à la classe `SearchItems`. Ce code gère l' <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> événement du <xref:System.Web.UI.WebControls.DropDownList> en appelant une méthode que vous allez créer ultérieurement dans cette procédure pas à pas.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Ajoutez les instructions suivantes en haut du fichier de code de la page d’application.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Ajoutez la méthode suivante à la classe `SearchItems`. Cette méthode itère au sein de tous les sites de la batterie de serveurs et recherche les éléments créés ou modifiés par l’utilisateur actuel.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Ajoutez la méthode suivante à la classe `SearchItems`. Cette méthode affiche les éléments créés ou modifiés par l’utilisateur actuel dans la table.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Tester la page de l’application

Lorsque vous exécutez le projet, le site SharePoint s’ouvre et la page application s’affiche.

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel de la page application, puis choisissez **définir comme élément de démarrage**.

2. Choisissez la touche **F5**.

     Le site SharePoint s’ouvre.

3. Sur la page application, choisissez l’option **modifié par moi** .

     La page d’application s’actualise et affiche tous les éléments que vous avez modifiés dans tous les sites de la batterie de serveurs.

4. Dans la page application, choisissez **créé par moi** dans la liste.

     La page d’application s’actualise et affiche tous les éléments que vous avez créés dans tous les sites de la batterie de serveurs.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les pages d’application SharePoint, consultez [créer des pages d’application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Pour plus d’informations sur la façon de concevoir du contenu de page SharePoint à l’aide de Visual Web Designer, consultez les rubriques suivantes :

- [Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Voir aussi

[Comment : créer une page](../sharepoint/how-to-create-an-application-page.md) 
 d’application [Type de page de _layouts d’application](/previous-versions/office/aa979604(v=office.14))
