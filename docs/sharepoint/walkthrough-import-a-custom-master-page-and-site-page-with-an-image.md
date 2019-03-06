---
title: 'Procédure pas à pas : Importation d’une Page maître personnalisée et de Page avec une Image de Site | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59dad7f376b79b2e8ac773f8cc604204dcd0c908
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602206"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Procédure pas à pas : Importer une page maître personnalisée et la page de site avec une image
  Cette procédure pas à pas montre comment importer une page maître personnalisée SharePoint et une page de site qui ont une image dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.

 Cette procédure pas à pas montre comment effectuer les tâches suivantes :

- Créer une page maître personnalisée et une page de site à l’aide d’une image dans SharePoint Designer.

- Exporter une page maître personnalisée, une image et une page de site à une solution SharePoint (*.wsp*) fichier.

- Importer et déployer le *.wsp* de fichiers dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint en utilisant le projet de Package de Solution SharePoint importation.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des composants suivants pour terminer cette procédure pas à pas :

-   Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

-   Visual Studio.

-   SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Créer des éléments dans SharePoint Designer
 Cet exemple montre comment créer trois éléments dans SharePoint Designer pour l’exportation : une page maître personnalisée, une page de site qui fait référence à la page maître personnalisée et un fichier image à afficher sur la page du site. L’image est ajoutée au dossier /images/ dans SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Pour créer une page maître personnalisée dans SharePoint Designer

1.  Dans SharePoint Designer, dans le volet de Navigation, choisissez le **Pages maîtres** objet de site.

2.  Sur le **Pages maîtres** ruban, choisissez **Page maître vierge**.

3.  Choisissez la nouvelle page maître, puis, dans le **Pages maîtres** ruban, choisissez **modifier le fichier**.

4.  En bas de SharePoint Designer, choisissez le **Code** onglet.

5.  Remplacez le balisage existant par le balisage suivant.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6.  Enregistrez la page, choisissez le **Pages maîtres** onglet et renommer la page maître en tant que **mybasic1.master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Ajouter une image à la base de données contenu dans SharePoint Designer
 Vous pouvez maintenant ajouter une image à afficher sur la page du site. L’image est déployée sur la base de données de contenu SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Pour ajouter une image à la base de données contenu dans SharePoint Designer

1.  Dans le volet de Navigation, choisissez le **tous les fichiers** objet de site et, dans l’arborescence de commandes, choisissez le **images** dossier.

2.  Sur le **tous les fichiers** ruban, choisissez **importer des fichiers**, choisissez un fichier de votre choix, puis le **OK** bouton. Dans cet exemple, le fichier est nommé **myimg1.png**.

     Si vous le souhaitez, vous pouvez créer un sous-dossier pour vous aider à organiser les images.

3.  Fermer le **importation** boîte de dialogue.

## <a name="create-a-site-page"></a>Créer une page de site
 Cette page de site de base utilise la page maître personnalisée et affiche l’image que vous avez ajouté à l’étape précédente.

#### <a name="to-create-a-site-page"></a>Pour créer une page de site

1.  Dans le volet de Navigation, choisissez le **Pages de Site** objet.

2.  Sur le **Pages** ruban, choisissez le **Page** bouton, choisissez la **ASPX** page, tapez, puis nommez le nouveau fichier **mycontentpage1.aspx**.

     Si vous le souhaitez, vous pouvez créer un sous-dossier pour vous aider à organiser les pages du site.

3.  Dans la liste de pages de site, choisissez **MyContentPage1.aspx** pour ouvrir sa page de propriétés, puis, en bas de la page, choisissez le **modifier le fichier** lien.

     Si un message s’affiche et indique que cette page ne contient pas toutes les régions qui sont modifiables en mode sans échec et vous demande si vous souhaitez ouvrir cette page en mode avancé, choisissez le **Oui** bouton.

4.  En bas de la page, choisissez le **Code** bouton.

5.  Remplacez le balisage existant par le balisage suivant.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6.  Enregistrez la page de site mis à jour.

## <a name="export-the-items-from-sharepoint"></a>Exporter les éléments à partir de SharePoint
 Exporter les éléments à partir de SharePoint à une solution SharePoint (*.wsp*) fichier.

#### <a name="to-export-items-from-sharepoint-designer"></a>Pour exporter des éléments à partir de SharePoint Designer

1.  Dans SharePoint Designer, dans le volet de Navigation, choisissez le **Site d’équipe** objet, puis, dans le **Site** ruban, choisissez **enregistrer comme modèle**.

2.  Dans le **enregistrer comme modèle** boîte de dialogue, entrez un nom de fichier et le nom du modèle, sélectionnez le **inclure du contenu** case à cocher, puis choisissez le **OK** bouton.

     Cette opération enregistre le contenu du site dans le *.wsp* fichier.

3.  Une fois que les exportations de la solution, choisissez le **galerie de solutions** lien pour afficher la liste des fichiers de solution disponible.

4.  Ouvrez le menu contextuel pour le nouveau *.wsp* de fichiers, puis choisissez **enregistrer la cible sous** à l’enregistrer dans le système.

## <a name="import-the-items-into-visual-studio"></a>Importer les éléments dans Visual Studio
 Importer le *.wsp* votre fichier en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Une fois que le contenu est importé, vous pouvez personnaliser il, ajouter d’autres éléments et ensuite de le déployer.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Pour importer des éléments à partir du fichier .wsp dans Visual Studio

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créer un **importer un Package SharePoint 2010 Solution** projet.

2. Sur le **sélectionner les éléments à importer** page sous **Module** dans le **Type** colonne, sélectionnez les cases à cocher pour que les fichiers dans le tableau suivant pour l’importation.


   | Nom du fichier | Description |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | La page maître personnalisée. |
   | images_ | Le fichier image dans le système de fichiers SharePoint. |
   | SitePages_ | La page du site. |


3. Choisissez le **Terminer** bouton pour importer les éléments sélectionnés.

4. Dans **l’Explorateur de solutions**, choisissez le \_catalogsmasterpage\_ nœud et définissez la valeur de son **Deployment Conflict Resolution** propriété **automatique** .

    Cela permet de garantir que les conflits de déploiement sont résolus automatiquement.

5. Si votre nouvelle page maître a le même nom qu’une page existante, assurez-vous que la page existante n’est pas marquée comme une Page maître par défaut ou une Page maître personnalisée dans SharePoint Designer.

    Si une page maître existante est marquée en tant que Page maître par défaut ou Page maître personnalisée, vous obtiendrez une erreur de déploiement qui stipule que la page maître ne peut pas être supprimée. Pour éviter ce problème, procédez comme suit :

   -   Si la page maître existante est définie en tant que Page maître par défaut, définissez temporairement une autre page maître en tant que Page maître par défaut. Après avoir déployé les fichiers sur SharePoint, définissez votre nouvelle page maître en tant que Page maître par défaut.

   -   Si la page maître existante est définie en tant que Page maître personnalisée, définissez temporairement une autre page maître en tant que Page maître personnalisée. Après avoir déployé les fichiers sur SharePoint, définissez votre nouvelle page maître en tant que Page maître personnalisée.

6. Dans la barre de menus, choisissez **Build** > **déployer la Solution**.

7. Ouvrez le site SharePoint pour afficher les éléments déployés.

   Une autre façon d’importer des fichiers dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et les déployer sur SharePoint consiste à ajouter les fichiers dans des modules dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Comment : Importer une page maître ou un thème](../sharepoint/how-to-import-a-master-page-or-theme.md) et [utiliser des modules pour inclure des fichiers dans la Solution](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Voir aussi
- [Importation d’éléments d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
