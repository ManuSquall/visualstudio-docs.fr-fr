---
title: "Procédure pas à pas : Création d’un projet de définition de Site de base | Documents Microsoft"
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 72a99a082fb1626013be6fa0ac5c759a43fd58a7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Procédure pas à pas : création d'un projet de définition de site de base
  Cette procédure pas à pas montre comment créer une définition de site de base qui contient un composant visual Web part avec certains contrôles sur celui-ci. Par souci de clarté, le composant visual WebPart que vous créez possède uniquement des contrôles. Toutefois, vous pouvez créer des définitions de site SharePoint plus sophistiquées qui incluent des fonctionnalités.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une définition de site à l’aide de la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modèle de projet.  
  
-   Création d’un site SharePoint à l’aide d’une définition de site dans SharePoint.  
  
-   Ajout d’un composant visual Web part à la solution.  
  
-   Personnalisation de la page du site default.aspx en y ajoutant le nouveau composant visual Web part.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Microsoft Windows et SharePoint. Pour plus d’informations, consultez Configuration requise pour le développement de Solutions SharePoint.  
  
-   Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Création d’une Solution de définition de Site  
 Commencez par créer le projet de définition de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Pour créer un projet de définition de site  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**. Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, dans la barre de menus, choisissez **fichier**, **nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Développez le **Visual C#** nœud ou la **Visual Basic** nœud, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
3.  Dans le **modèles** , choisissez le **projet SharePoint 2010** modèle.  
  
4.  Dans le **nom** , entrez **TestSiteDef**, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
5.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez l’URL pour le site SharePoint où vous souhaitez déboguer la définition de site ou utilisez l’emplacement par défaut (http://*nom système*/).  
  
6.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer une solution de batterie de serveurs** case d’option.  
  
     Tous les projets de définition de site doivent être déployés en tant que solutions de batterie de serveurs. Pour plus d’informations sur les solutions bac à sable par rapport aux solutions de batterie de serveurs, consultez [considérations sur les solutions bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Choisissez le **Terminer** bouton.  
  
     Le projet s’affiche dans **l’Explorateur de solutions**.  
  
8.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
9. Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
10. Dans le **modèles** volet, choisissez la **définition de Site** modèle, laissez le **nom** en tant que **SiteDefinition1**, puis choisissez le  **Ajouter** bouton.  
  
## <a name="create-a-visual-web-part"></a>Créer un composant Visual Web Part  
 Ensuite, créez un composant visual WebPart pour qu’il apparaisse sur la page principale de la définition de site.  
  
#### <a name="to-create-a-visual-web-part"></a>Pour créer un composant visual Web part  
  
1.  Dans **l’Explorateur de solutions**, choisissez le **afficher tous les fichiers** bouton.  
  
2.  Choisissez le **SiteDefinition1** nœud de projet, puis, dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
3.  Développez le **Visual C#** nœud ou la **Visual Basic** nœud, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans la liste des modèles, choisissez le **composant Visual Web Part** modèle, conservez la valeur par défaut VisualWebPart1 de nom, puis choisissez le **ajouter** bouton.  
  
     Le fichier VisualWebPart1.ascx s’ouvre.  
  
5.  Au bas de VisualWebPart1.ascx, ajoutez le balisage suivant pour ajouter trois contrôles au formulaire : une zone de texte, un bouton et une étiquette :  
  
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
  
6.  Sous VisualWebPart1.ascx, ouvrez le fichier VisualWebPart1.ascx.cs (pour [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) ou VisualWebPart1.ascx.vb (pour [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), puis ajoutez le code suivant :  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Ce code ajoute des fonctionnalités pour sur un bouton du composant.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Ajouter le composant Visual Web Part à la Page ASPX par défaut  
 Ensuite, ajoutez le composant visual Web part à la page ASPX de la définition site par défaut.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Pour ajouter un composant visual Web part à la page ASPX par défaut  
  
1.  Ouvrez la page default.aspx, puis ajoutez la ligne suivante sous la `WebPartPages` balise :  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Cette ligne associe le nom MyWebPartControls avec le composant WebPart et son code. Le *Namespace* paramètre correspond à l’espace de noms qui est utilisé dans le fichier de code VisualWebPart1.ascx.  
  
2.  Après le `</asp:Content>` élément, remplacez l’intégralité de `ContentPlaceHolderId="PlaceHolderMain"` section et son contenu par le code suivant :  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Ce code crée une référence à un composant visual Web part que vous avez créé précédemment.  
  
3.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SiteDefinition1** nœud, puis choisissez **définir comme élément de démarrage**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Déployer et exécuter la solution de définition de site  
 Ensuite, déployez le projet vers SharePoint et puis exécutez le projet.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Pour déployer et exécuter la définition de site  
  
-   Dans la barre de menus, choisissez **générer**, **TestSiteDef de déployer**.  
  
-   Appuyez sur la touche F5.  
  
     Visual Studio compile le code, ajoute ses fonctionnalités, empaquette tous les fichiers dans un fichier de solution (WSP) de SharePoint et déploie le fichier WSP pour SharePoint Server. SharePoint installe ensuite les fichiers, puis active les fonctionnalités.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Créer un Site basé sur la définition de Site  
 Ensuite, créez un site à l’aide de la nouvelle définition de site.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Pour créer un site à l’aide de la définition de site  
  
1.  Sur le site SharePoint, la page Nouveau SharePoint Site s’affiche.  
  
2.  Dans le **Title et Description** section, entrez **mon nouveau Site** pour le titre et une description du site.  
  
3.  Dans le **adresse de Site Web** section, entrez **monnouveausite** dans les **nom de l’URL** boîte.  
  
4.  Dans le **modèle** , choisissez le **personnalisations de SharePoint** onglet.  
  
5.  Dans le **sélectionner un modèle** , choisissez **SiteDefinition1**.  
  
6.  Conservez les autres paramètres à leurs valeurs par défaut, puis choisissez le **créer** bouton.  
  
     Le nouveau site s’affiche.  
  
## <a name="test-the-new-site"></a>Tester le nouveau Site  
 Ensuite, testez le nouveau site pour vérifier qu’il fonctionne correctement.  
  
#### <a name="to-test-the-new-site"></a>Pour tester le nouveau site  
  
-   Dans la page ASPX par défaut, entrez du texte, puis choisissez le **modifier le texte étiquette** bouton en regard de la zone de texte.  
  
     Le texte apparaît dans l’étiquette située à droite du bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  