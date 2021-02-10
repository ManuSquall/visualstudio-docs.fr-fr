---
title: 'Procédure pas à pas : création d’un projet de définition de site de base | Microsoft Docs'
description: Dans cette procédure pas à pas SharePoint, consultez Comment créer une définition de site de base contenant un composant Visual Web part avec des contrôles.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: def1ae862a7b9ba4def62cb590260c5a18758929
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937704"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Procédure pas à pas : création d’un projet de définition de site de base
  Cette procédure pas à pas vous montre comment créer une définition de site de base contenant un composant Visual Web part avec des contrôles. Par souci de clarté, le composant Visual Web part que vous créez n’a que quelques contrôles. Toutefois, vous pouvez créer des définitions de site SharePoint plus sophistiquées qui incluent davantage de fonctionnalités.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une définition de site à l’aide du [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modèle de projet.

- Création d’un site SharePoint à l’aide d’une définition de site dans SharePoint.

- Ajout d’un composant Visual Web part à la solution.

- Personnalisation de la page default. aspx du site en y ajoutant le nouveau composant Visual Web part.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Microsoft Windows et SharePoint. Pour plus d’informations, consultez Configuration requise pour le développement de solutions SharePoint.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Créer une solution de définition de site
 Tout d’abord, créez le projet de définition de site dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Pour créer un projet de définition de site

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**. Si votre IDE est configuré pour utiliser Visual Basic paramètres de développement, dans la barre de menus, choisissez **fichier**  >  **nouveau projet**.

    La boîte de dialogue **Nouveau projet** apparaît.

2. Développez le nœud **Visual C#** ou le nœud **Visual Basic** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

3. Dans la liste **modèles** , choisissez le modèle de **projet SharePoint 2010** .

4. Dans la zone **nom** , entrez **TestSiteDef**, puis choisissez le bouton **OK** .

    L' **Assistant Personnalisation de SharePoint** s’affiche.

5. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , entrez l’URL du site SharePoint où vous souhaitez déboguer la définition de site, ou utilisez l’emplacement par défaut (<em>nom système</em>http:///).

6. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez la case **d’option déployer en tant que solution de batterie** .

    Tous les projets de définition de site doivent être déployés en tant que solutions de batterie. Pour plus d’informations sur les solutions sandbox et les solutions de batterie de serveurs, consultez Considérations sur les solutions [bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

7. Cliquez sur le bouton **Terminer**.

    Le projet s’affiche dans **Explorateur de solutions**.

8. Dans **Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

9. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

10. Dans le volet **modèles** , choisissez le modèle de **définition de site** , laissez le **nom** **SiteDefinition1**, puis cliquez sur le bouton **Ajouter** .

## <a name="create-a-visual-web-part"></a>Créer un composant Visual Web part
 Ensuite, créez un composant Visual Web part pour qu’il apparaisse sur la page principale de la définition de site.

#### <a name="to-create-a-visual-web-part"></a>Pour créer un composant Visual Web part

1. Dans **Explorateur de solutions**, choisissez le bouton **Afficher tous les fichiers** .

2. Choisissez le nœud de projet **SiteDefinition1** , puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.

3. Développez le nœud **Visual C#** ou le nœud **Visual Basic** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

4. Dans la liste des modèles, choisissez le modèle **Visual Web part** , conservez le nom par défaut VisualWebPart1, puis cliquez sur le bouton **Ajouter** .

     Le fichier *VisualWebPart1. ascx* s’ouvre.

5. En bas de *VisualWebPart1. ascx*, ajoutez le balisage suivant pour ajouter trois contrôles au formulaire : une zone de texte, un bouton et une étiquette :

    ```aspx-csharp
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

6. Sous *VisualWebPart1. ascx*, ouvrez le fichier *VisualWebPart1.ascx.cs* (pour [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) ou *VisualWebPart1. ascx. vb* (pour [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), puis ajoutez le code suivant :

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Ce code ajoute des fonctionnalités pour le clic de bouton du composant WebPart.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Ajouter le composant Visual Web part à la page ASPX par défaut
 Ensuite, ajoutez le composant Visual Web part à la page ASPX par défaut de la définition de site.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Pour ajouter un composant Visual Web part à la page ASPX par défaut

1. Ouvrez la page default. aspx, puis ajoutez la ligne suivante sous la `WebPartPages` balise :

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Cette ligne associe le nom MyWebPartControls au composant WebPart et à son code. Le paramètre d' *espace de noms* correspond à l’espace de noms utilisé dans le fichier de code *VisualWebPart1. ascx* .

2. Après l' `</asp:Content>` élément, remplacez la totalité de la `ContentPlaceHolderId="PlaceHolderMain"` section et son contenu par le code suivant :

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Ce code crée une référence au composant Visual Web part que vous avez créé précédemment.

3. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **SiteDefinition1** , puis choisissez **définir comme élément de démarrage**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Déployer et exécuter la solution de définition de site
 Ensuite, déployez le projet sur SharePoint, puis exécutez le projet.

#### <a name="to-deploy-and-run-the-site-definition"></a>Pour déployer et exécuter la définition de site

- Dans la barre de menus, choisissez **générer**  >  **déployer TestSiteDef**.

- Choisissez la touche **F5**.

     Visual Studio compile le code, ajoute ses fonctionnalités, empaquette tous les fichiers dans un fichier de solution SharePoint (WSP) et déploie le fichier WSP sur le serveur SharePoint. SharePoint installe ensuite les fichiers, puis active les fonctionnalités.

## <a name="create-a-site-based-on-the-site-definition"></a>Créer un site basé sur la définition de site
 Ensuite, créez un site à l’aide de la nouvelle définition de site.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Pour créer un site à l’aide de la définition de site

1. Sur le site SharePoint, la page nouveau site SharePoint s’affiche.

2. Dans la section **titre et description** , entrez **mon nouveau site** pour le titre et une description du site.

3. Dans la section **adresse du site Web** , entrez **mynewsite** dans la zone nom de l' **URL** .

4. Dans la section **modèle** , choisissez l’onglet **personnalisations SharePoint** .

5. Dans la liste **Sélectionner un modèle** , choisissez **SiteDefinition1**.

6. Laissez les autres paramètres à leurs valeurs par défaut, puis choisissez le bouton **créer** .

     Le nouveau site s’affiche.

## <a name="test-the-new-site"></a>Tester le nouveau site
 Ensuite, testez le nouveau site pour vérifier s’il fonctionne correctement.

#### <a name="to-test-the-new-site"></a>Pour tester le nouveau site

- Sur la page ASPX par défaut, entrez du texte, puis choisissez le bouton **modifier le texte** de l’étiquette en regard de la zone de texte.

     Le texte s’affiche dans l’étiquette sur le côté droit du bouton.

## <a name="see-also"></a>Voir aussi
- [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
