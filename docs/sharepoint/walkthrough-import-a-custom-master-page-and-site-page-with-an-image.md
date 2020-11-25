---
title: Importer une page maître personnalisée & page de site avec une image
description: Dans cette procédure pas à pas, importez une page maître personnalisée SharePoint et une page de site qui contient une image dans un projet SharePoint Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 7ceb69608a2d1770f082991f3d927d4e4639ae56
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970155"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Procédure pas à pas : importer une page maître et une page de site personnalisées avec une image
  Cette procédure pas à pas montre comment importer une page maître personnalisée SharePoint et une page de site qui contient une image dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.

 Cette procédure pas à pas montre comment effectuer les tâches suivantes :

- Créez une page maître personnalisée et une page de site à l’aide d’une image dans SharePoint Designer.

- Exporter une page maître, une image et une page de site personnalisées vers un fichier de solution SharePoint (*. wsp*).

- Importez et déployez le fichier *. wsp* dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint à l’aide du projet importer le package de solution SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Créer des éléments dans SharePoint Designer
 Cet exemple montre comment créer trois éléments dans SharePoint Designer pour l’exportation : une page maître personnalisée, une page de site qui fait référence à la page maître personnalisée et un fichier image à afficher sur la page de site. L’image est ajoutée au dossier/images/dans SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Pour créer une page maître personnalisée dans SharePoint Designer

1. Dans SharePoint Designer, dans le volet de navigation, choisissez l’objet de site **pages maîtres** .

2. Dans le ruban **pages maîtres** , choisissez **page maître vide**.

3. Choisissez la nouvelle page maître, puis, dans le ruban **pages maîtres** , choisissez **modifier le fichier**.

4. En bas de SharePoint Designer, choisissez l’onglet **code** .

5. Remplacez le balisage existant par le balisage suivant.

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

6. Enregistrez la page, choisissez l’onglet **pages maîtres** , puis renommez la page maître en **mybasic1. Master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Ajouter une image à la base de données de contenu dans SharePoint Designer
 Vous pouvez maintenant ajouter une image à afficher sur la page du site. L’image est déployée dans la base de données de contenu SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Pour ajouter une image à la base de données de contenu dans SharePoint Designer

1. Dans le volet de navigation, choisissez l’objet site **tous les fichiers** , puis, dans l’arborescence, choisissez le dossier **images** .

2. Dans le ruban **tous les fichiers** , choisissez **importer des fichiers**, choisissez un fichier de votre choix, puis choisissez le bouton **OK** . Dans cet exemple, le fichier est nommé **myimg1.png**.

     Si vous le souhaitez, vous pouvez créer un sous-dossier pour faciliter l’Organisation des images.

3. Fermez la boîte de dialogue **Importer** .

## <a name="create-a-site-page"></a>Créer une page de site
 Cette page de site de base utilise la page maître personnalisée et affiche l’image que vous avez ajoutée à l’étape précédente.

#### <a name="to-create-a-site-page"></a>Pour créer une page de site

1. Dans le volet de navigation, choisissez l’objet **pages de site** .

2. Dans le ruban **pages** , choisissez le bouton **page** , choisissez le type de page **aspx** , puis nommez le nouveau fichier **MyContentPage1. aspx**.

     Si vous le souhaitez, vous pouvez créer un sous-dossier pour faciliter l’Organisation des pages du site.

3. Dans la liste pages de site, choisissez **MyContentPage1. aspx** pour ouvrir sa page de propriétés, puis, en bas de la page, choisissez le lien **modifier le fichier** .

     Si un message s’affiche et indique que cette page ne contient aucune région modifiable en mode sans échec et vous demande si vous souhaitez ouvrir cette page en mode avancé, choisissez le bouton **Oui** .

4. En bas de la page, cliquez sur le bouton **code** .

5. Remplacez le balisage existant par le balisage suivant.

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

6. Enregistrez la page de site mise à jour.

## <a name="export-the-items-from-sharepoint"></a>Exporter les éléments à partir de SharePoint
 Exportez les éléments de SharePoint vers un fichier de solution SharePoint (*. wsp*).

#### <a name="to-export-items-from-sharepoint-designer"></a>Pour exporter des éléments à partir de SharePoint Designer

1. Dans SharePoint Designer, dans le volet de navigation, choisissez l’objet **site d’équipe** , puis, dans le ruban **site** , choisissez **enregistrer en tant que modèle**.

2. Dans la boîte de dialogue **Enregistrer comme modèle** , entrez un nom de fichier et un nom de modèle, activez la case à cocher **inclure le contenu** , puis choisissez le bouton **OK** .

     Cela permet d’enregistrer le contenu du site dans le fichier *. wsp* .

3. Une fois la solution exportée, cliquez sur le lien de la **Galerie de solutions** pour afficher la liste des fichiers de solution disponibles.

4. Ouvrez le menu contextuel du nouveau fichier *. wsp* , puis choisissez **enregistrer la cible sous** pour l’enregistrer sur le système.

## <a name="import-the-items-into-visual-studio"></a>Importer les éléments dans Visual Studio
 Importez le fichier *. wsp* dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Une fois le contenu importé, vous pouvez le personnaliser, ajouter des éléments, puis le déployer.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Pour importer des éléments à partir du fichier. wsp dans Visual Studio

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , créez un projet d' **importation de package de Solution SharePoint 2010** .

2. Dans la page **Sélectionner les éléments à importer** , sous **module** dans la colonne **type** , activez les cases à cocher uniquement pour les fichiers dans le tableau suivant pour l’importation.

   | Nom de fichier | Description |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Page maître personnalisée. |
   | images_ | Fichier image dans le système de fichiers SharePoint. |
   | SitePages_ | Page du site. |

3. Cliquez sur le bouton **Terminer** pour importer les éléments sélectionnés.

4. Dans **Explorateur de solutions**, choisissez le \_ \_ nœud catalogsmasterpage, puis définissez la valeur de sa propriété **résolution de conflit de déploiement** sur **automatique**.

    Cela permet de s’assurer que les conflits de déploiement sont résolus automatiquement.

5. Si votre nouvelle page maître porte le même nom qu’une page existante, assurez-vous que la page existante n’est pas marquée comme page maître par défaut ou comme page maître personnalisée dans SharePoint Designer.

    Si une page maître existante est marquée comme page maître par défaut ou page maître personnalisée, vous obtiendrez une erreur de déploiement indiquant que la page maître ne peut pas être supprimée. Pour éviter ce problème, procédez comme suit :

   - Si la page maître existante est définie en tant que page maître par défaut, définissez temporairement une autre page maître comme page maître par défaut. Une fois que vous avez déployé les fichiers sur SharePoint, définissez votre nouvelle page maître comme page maître par défaut.

   - Si la page maître existante est définie en tant que page maître personnalisée, définissez temporairement une autre page maître comme page maître personnalisée. Une fois que vous avez déployé les fichiers sur SharePoint, définissez votre nouvelle page maître comme page maître personnalisée.

6. Dans la barre de menus, choisissez **générer**  >  **déployer la solution**.

7. Ouvrez le site SharePoint pour afficher les éléments déployés.

   Une autre façon d’importer des fichiers dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et de les déployer sur SharePoint consiste à ajouter les fichiers dans des modules dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Comment : importer une page maître ou un thème](../sharepoint/how-to-import-a-master-page-or-theme.md) et [utiliser des modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Voir aussi
- [Importation d’éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
