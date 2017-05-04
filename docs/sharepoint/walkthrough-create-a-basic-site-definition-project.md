---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un projet de d&#233;finition de site de base | Microsoft Docs"
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
  - "développement SharePoint dans Visual Studio, définitions de sites"
  - "définitions de sites (développement SharePoint dans Visual Studio)"
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un projet de d&#233;finition de site de base
  Cette procédure pas à pas montre comment créer une définition de site de base constituée d'un composant Visual Web Part où figurent plusieurs contrôles.  Pour des raisons de simplicité, le composant Visual Web Part que vous allez concevoir comportera juste quelques contrôles.  Rien ne vous empêche évidemment de créer des définitions de site SharePoint plus sophistiquées mettant en jeu un grand nombre de fonctionnalités.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une définition de site à l'aide du modèle de projet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Création d'un site SharePoint en utilisant une définition de site dans SharePoint.  
  
-   Ajout d'un composant Visual Web Part à la solution.  
  
-   Personnalisation de la page default.aspx du site en lui ajoutant le nouveau composant Visual Web Part.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de Microsoft Windows et SharePoint prises en charge.  Pour plus d'informations, consultez la rubrique Configuration requise pour développer des solutions SharePoint.  
  
-   Visual Studio.  
  
## Création d'une solution de définition de site  
 Commencez par créer le projet de définition de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Pour créer un projet de définition de site  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, dans la barre de menu cliquez sur **Fichier**, puis **Nouveau Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Développez le nœud **Visual C\#** ou le nœud **Visual Basic**, développez le nœud **SharePoint**, puis choisissez le nœud **2010**.  
  
3.  Dans la liste de **Modèles**, sélectionnez le modèle **Projet SharePoint 2010**.  
  
4.  Dans la zone de texte **Nom**, entrez TestSiteDef, puis choisissez le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
5.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez l'URL du site du serveur SharePoint où vous souhaitez déboguer la définition de site, ou utilisez l'emplacement par défaut \(http:\/\/*System Name*\/\).  
  
6.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, choisissez la case d'option **Déployer en tant que solution de batterie**.  
  
     Tous les projets de définition de site doivent être déployés comme solutions de batterie.  Pour plus d'informations sur les différences entre les solutions bac à sable \(sandbox\) et les solutions de batterie, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Choisissez le bouton **Terminer**.  
  
     Le projet s'affiche dans l'**Explorateur de solutions**.  
  
8.  Dans l'**Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **Project**, **Ajouter un nouvel objet**.  
  
9. Sous **Visual C\#** ou **Visual Basic**, développez le nœud **SharePoint**, puis cliquez sur le noeud **2010**.  
  
10. Dans le volet de **Modèles**, sélectionnez le modèle **Définition de site**, laissez la valeur de **Nom** à **SiteDefinition1**, puis cliquez sur le bouton **Ajouter**.  
  
## Création d'un composant Visual Web Part  
 Créez maintenant un composant Visual Web Part afin de l'afficher dans la page principale de définition du site.  
  
#### Pour créer un composant Visual Web Part  
  
1.  Dans l'**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.  
  
2.  Sélectionnez le nœud de projet **SiteDefinition1**, puis, dans la barre de menus, cliquez sur **Projet**, **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.  
  
3.  Développez le nœud **Visual C\#** ou le nœud **Visual Basic**, développez le nœud **SharePoint**, puis choisissez le nœud **2010**.  
  
4.  Dans la liste de modèles, sélectionnez le modèle **Composant Visual Web Part**, conservez le nom par défaut VisualWebPart1, puis cliquez sur le bouton **Ajouter**.  
  
     Le fichier VisualWebPart1.ascx s'ouvre.  
  
5.  En bas du fichier VisualWebPart1.ascx, insérez les balises suivantes afin d'ajouter trois contrôles au formulaire, c'est\-à\-dire, une zone de texte, un bouton et une étiquette :  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  Sous VisualWebPart1.ascx, ouvrez le fichier VisualWebPart1.ascx.cs \(pour [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\) ou VisualWebPart1.ascx.vb \(pour [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) situé sous VisualWebPart1UserControl.ascx, puis ajoutez le code suivant :  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     Ce code ajoute la fonctionnalité correspondant à l'action de cliquer sur le bouton du composant WebPart.  
  
## Ajout du composant Visual Web Part à la page ASPX par défaut  
 Il convient, à présent, d'ajouter le composant Visual Web Part à la page ASPX par défaut de la définition de site.  
  
#### Pour ajouter un composant Visual Web Part à la page ASPX par défaut  
  
1.  Ouvrez la page default.aspx et insérez la ligne suivante sous la balise `WebPartPages`.  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Cette ligne associe le nom MyWebPartControls au composant Web Part et à son code.  Le paramètre *Namespace* correspond à l'espace de noms utilisé dans le fichier de code de VisualWebPart1.ascx.  
  
2.  Après l'élément `</asp:Content>`, remplacez toute la section `ContentPlaceHolderId="PlaceHolderMain"` et son contenu par le code suivant :  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Ce code permet d'associer une référence au composant Visual Web Part que vous avez créé précédemment.  
  
3.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du nœud **SiteDefinition1**, puis choisissez **Définir comme élément de démarrage**.  
  
## Déployer et exécuter la solution de définition de site  
 Ensuite, déployez le projet SharePoint, puis exécutez le projet.  
  
#### Pour déployer et exécuter la définition de site  
  
-   Dans la barre de menus, choisissez **Générer**, puis **Déployer TestSiteDef**.  
  
-   Appuyez sur la touche F5.  
  
     Visual Studio compile le code, ajoute ses fonctionnalités, empaquette tous les fichiers dans un fichier de solution SharePoint \(WSP\) et déploie le fichier WSP sur le serveur SharePoint.  SharePoint se charge ensuite d'installer les fichiers et d'activer les fonctionnalités.  
  
## Création d'un site basé sur la définition de site  
 Vous allez maintenant créer un site en vous basant sur la nouvelle définition de site.  
  
#### Pour créer un site à l'aide de la définition de site  
  
1.  Sur le site SharePoint, la page Nouveau site SharePoint s'affiche.  
  
2.  Dans la section **Titre et description**, tapez Mon nouveau site en guise de titre et de description du site.  
  
3.  Dans la section **Adresse du site Web**, entrez monnouveausite dans la zone **Nom de l'URL**.  
  
4.  Dans la section **Modèle**, choisissez l'onglet de **Personnalisations SharePoint**.  
  
5.  Dans la liste **Sélectionner un modèle**, choisissez **SiteDefinition1**.  
  
6.  Conservez les valeurs par défaut des autres paramètres, puis cliquez sur le bouton **Créer**.  
  
     Le nouveau site apparaît.  
  
## Test du nouveau site  
 Pour finir, testez le nouveau site afin de vous assurer qu'il fonctionne correctement.  
  
#### Pour tester le nouveau site  
  
-   Dans la page par défaut ASPX, entrez du texte, puis cliquez sur le bouton **Changer l'étiquette de texte** à côté de la zone de texte.  
  
     Le texte s'affiche dans l'étiquette à droite du bouton.  
  
## Voir aussi  
 [Comment : créer un récepteur d'événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  