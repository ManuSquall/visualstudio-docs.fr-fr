---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une page d&#39;application SharePoint"
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
  - "pages d’application (développement SharePoint dans Visual Studio), développement"
  - "pages d’application (développement SharePoint dans Visual Studio), création"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une page d&#39;application SharePoint
  Une page d'application désigne une forme spécifique de page ASP.NET.  Les pages d'application comportent du contenu qui est fusionné avec une page maître SharePoint.  Pour plus d'informations, consultez [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Cette procédure pas à pas vous indique comment créer une page d'application et la déboguer à l'aide d'un site SharePoint local.  Cette page affiche tous les éléments que chaque utilisateur a créés ou modifiés dans tous les sites de la batterie de serveurs.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet SharePoint  
  
-   Ajout d'une page d'application au projet SharePoint  
  
-   Ajout de contrôles ASP.NET à la page d'application  
  
-   Ajout de code\-behind aux contrôles ASP.NET  
  
-   Test de la page d'application  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] ou une édition de Visual Studio Ultimate ou Visual Studio Premium.  
  
## Création d'un projet SharePoint  
 Commencez par créer un **Projet SharePoint vide**.  Vous ajouterez ensuite un élément **Page Application** à ce projet.  
  
#### Pour créer un projet SharePoint  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Ouvrez la boîte de dialogue **Nouveau projet**, développez le nœud **Office\/SharePoint** sous le langage que vous souhaitez utiliser, puis choisissez le nœud **Solutions SharePoint**.  
  
3.  Dans le volet **Modèles Visual Studio installés**, choisissez le modèle **SharePoint 2010 \- Projet vide**.  Nommez le projet MySharePointProject, puis cliquez sur **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  Cet Assistant vous permet de sélectionner le site à utiliser pour déboguer le projet et le niveau de confiance de la solution.  
  
4.  Sélectionnez la case d'option **Déployer en tant que solution de batterie**, puis choisissez le bouton **Terminer** pour accepter le site SharePoint local par défaut.  
  
## Création d'une page d'application  
 Pour créer une page d'application, ajoutez un élément **Page Application** au projet.  
  
#### Pour créer une page d'application  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez le projet **MySharePointProject**.  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le modèle **Page Application \(solution de batterie uniquement\)**.  
  
4.  Nommez la page SearchItems, puis choisissez le bouton **Ajouter**.  
  
     Le concepteur Visual Web Developer affiche la page d'application en mode **Source**  ; vous pouvez ainsi consulter les éléments HTML de la page.  Le concepteur affiche le balisage de plusieurs contrôles <xref:System.Web.UI.WebControls.Content>.  Chaque contrôle est mappé à un contrôle <xref:System.Web.UI.WebControls.ContentPlaceHolder> qui est défini dans la page d'application maître par défaut.  
  
## Conception de la disposition de la page d'application  
 L'élément Page Application vous permet d'utiliser un concepteur pour ajouter des contrôles ASP.NET à la page d'application.  Ce concepteur est le même que celui utilisé dans Visual Web Developer.  Ajoutez une étiquette, une liste Case d'option et une table sur le concepteur en mode **Source**, puis définissez les propriétés comme lorsque vous concevez une page ASP.NET standard.  
  
 Pour plus d'informations sur l'utilisation du concepteur dans Visual Web Developer, consultez [Visual Studio Web Development Content Map](http://msdn.microsoft.com/fr-fr/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
#### Pour concevoir la disposition de la page d'application  
  
1.  Dans la barre de menus, choisissez **Affichage**, **Boîte à outils**.  
  
2.  Dans le nœud standard de la **Boîte à outils**, effectuez l'une des opérations suivantes :  
  
    -   Ouvrez le menu contextuel de l'élément **Étiquette**, choisissez **Copier**, ouvrez le menu contextuel de la ligne située sous le contrôle de contenu **PlaceHolderMain** dans le concepteur, puis choisissez **Coller**.  
  
    -   Faites glisser l'élément **Étiquette** de la **Boîte à outils** sur le corps du contrôle de contenu **PlaceHolderMain**.  
  
3.  Répétez l'étape précédente afin d'ajouter un élément **DropDownList** et un élément **Table** au contrôle de contenu **PlaceHolderMain**.  
  
4.  Dans le concepteur, affectez la valeur Afficher tous les éléments à l'attribut `Text` du contrôle d'étiquette.  
  
5.  Dans le concepteur, remplacez l'élément `<asp:DropDownList>` par le code XML suivant.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## Gestion des événements de contrôles dans la page  
 Vous pouvez gérer les contrôles dans une page d'application de la même manière que vous le feriez dans une page ASP.NET.  Dans cette procédure, vous allez générer l'événement `SelectedIndexChanged` dans la liste déroulante.  
  
#### Pour gérer les événements de contrôles dans la page  
  
1.  Dans le menu **Affichage**, choisissez **Code**.  
  
     Le fichier de code de la page d'application s'ouvre dans l'éditeur de code.  
  
2.  Ajoutez la méthode suivante à la classe `SearchItems`.  Ce code gère l'événement <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> du <xref:System.Web.UI.WebControls.DropDownList> en appelant une méthode que vous créerez plus loin dans cette procédure.  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  Ajoutez les instructions suivantes au début du fichier de code de la page d'application.  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  Ajoutez la méthode suivante à la classe `SearchItems`.  Cette méthode itère au sein de l'ensemble des sites de la batterie de serveurs et recherche les éléments créés ou modifiés par l'utilisateur actuel.  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  Ajoutez la méthode suivante à la classe `SearchItems`.  Cette méthode affiche les éléments créés ou modifiés par l'utilisateur actuel dans la table.  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## Test de la page d'application  
 Lorsque vous exécutez le projet, le site SharePoint s'ouvre et la page d'application s'affiche.  
  
#### Pour tester la page d'application  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de la page d'application, puis choisissez **Définir comme élément de démarrage**.  
  
2.  Sélectionnez la touche F5.  
  
     Le site SharePoint s'ouvre.  
  
3.  Dans la page d'application, cliquez sur l'option **Modifiés par moi**.  
  
     La page d'application s'actualise et affiche tous les éléments que vous avez modifiés dans l'ensemble des sites de la batterie de serveurs.  
  
4.  Dans la page d'application, choisissez **Que j'ai créés** dans la liste.  
  
     La page d'application s'actualise et affiche tous les éléments que vous avez créés dans l'ensemble des sites de la batterie de serveurs.  
  
## Étapes suivantes  
 Pour plus d'informations au sujet des pages d'application SharePoint, consultez [Création de pages d'application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Pour savoir comment concevoir le contenu d'une page SharePoint à l'aide de Visual Web Designer, consultez les rubriques suivantes :  
  
-   [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Voir aussi  
 [Comment : créer une page d'application](../sharepoint/how-to-create-an-application-page.md)   
 [Type de page de dispositions d'application](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  