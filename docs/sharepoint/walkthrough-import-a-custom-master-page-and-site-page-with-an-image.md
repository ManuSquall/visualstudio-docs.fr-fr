---
title: "Proc&#233;dure pas &#224; pas&#160;: importation d&#39;une page ma&#238;tre et d&#39;une page de site personnalis&#233;es avec une image"
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
helpviewer_keywords: 
  - "importer des éléments (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, importer des éléments"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Proc&#233;dure pas &#224; pas&#160;: importation d&#39;une page ma&#238;tre et d&#39;une page de site personnalis&#233;es avec une image
  Cette procédure pas à pas explique comment importer une page maître personnalisée SharePoint et une page de site qui ont une image dans un projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Cette procédure pas à pas montre comment effectuer les tâches suivantes :  
  
-   Créer une page maître personnalisée et une page de site à l'aide d'une image dans SharePoint Designer.  
  
-   Exporter une page maître personnalisée, une image et une page de site vers un fichier de solution SharePoint \(.wsp\).  
  
-   Importer et déployer le fichier .wsp dans un projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à l'aide du projet Importer le package de solution SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Vous devez disposer des composants suivants pour terminer cette procédure pas à pas :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et de SharePoint prises en charge.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## Créer des éléments dans SharePoint Designer  
 Cet exemple indique comment créer trois éléments dans SharePoint Designer pour l'exportation : une page maître personnalisée, une page de site qui référence la page maître personnalisée, et un fichier image à afficher dans la page de site.  L'image est ajoutée au dossier \/images\/ dans SharePoint.  
  
#### Pour créer une page maître personnalisée dans SharePoint Designer  
  
1.  Dans SharePoint Designer, dans le volet Navigation, cliquez sur l'objet de site **Pages maîtres**.  
  
2.  Dans le ruban **Pages maîtres**, choisissez **Page maître vide**.  
  
3.  Choisissez la nouvelle page maître, puis, dans le ruban **Pages maîtres**, choisissez **Fichier de modification**.  
  
4.  En bas de SharePoint Designer, cliquez sur l'onglet **Code**.  
  
5.  Remplacez la balise existante par la balise suivante.  
  
    ```  
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
  
6.  Enregistrez la page, sélectionnez l'onglet **Pages maîtres**, et renommez la page maître comme **mybasic1.master**.  
  
## Ajouter une image à la base de données de contenu dans SharePoint Designer  
 À présent, vous pouvez ajouter une image à afficher dans la page de site.  L'image est déployée sur la base de données de contenu SharePoint.  
  
#### Pour ajouter une image à la base de données de contenu dans SharePoint Designer  
  
1.  Dans le volet de navigation, choisissez l'objet de site **Tous les fichiers**, puis, dans l'arborescence, sélectionnez le dossier **Images**.  
  
2.  Dans le ruban **Tous les fichiers**, choisissez **Fichiers d'importation**, choisissez un fichier de votre choix, puis cliquez sur le bouton **OK**.  Dans cet exemple, le fichier est nommé **myimg1.png**.  
  
     Vous pouvez également créer un sous\-dossier dans lequel organiser les images.  
  
3.  Fermez la boîte de dialogue **Importer**.  
  
## Créer une page de site  
 Cette page de site de base utilise la page maître personnalisée et affiche l'image que vous avez ajoutée à l'étape précédente.  
  
#### Pour créer une page de site  
  
1.  Dans le volet de navigation, choisissez l'objet **Pages de site**.  
  
2.  Dans le ruban **Pages**, cliquez sur le bouton **Page**, choisissez le type **ASPX**, puis nommez le nouveau fichier **mycontentpage1.aspx**.  
  
     Vous pouvez également créer un sous\-dossier dans lequel organiser les pages de site.  
  
3.  Dans la liste des pages du site, cliquez sur **MyContentPage1.aspx** pour ouvrir sa page de propriétés, puis, en bas de page, cliquez sur le lien **Modifier le fichier**.  
  
     Si un message apparaît et indique que cette page ne contient aucune région qui est modifiable en mode sans erreur et ne demande pas si vous souhaitez ouvrir cette page en mode avancé, cliquez sur le bouton **Oui**.  
  
4.  En bas de la page, cliquez sur le bouton **Code**.  
  
5.  Remplacez la balise existante par la balise suivante.  
  
    ```  
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
  
6.  Enregistrez la page de site mise à jour.  
  
## Exporter les éléments de SharePoint  
 Exportez les éléments de SharePoint vers un fichier solution SharePoint \(.wsp\).  
  
#### Pour exporter des éléments de SharePoint Designer  
  
1.  Dans SharePoint Designer, dans le volet de navigation, choisissez l'objet **Team Site**, puis, dans le ruban **Site**, choisissez **Enregistrer comme modèle**.  
  
2.  Dans la boîte de dialogue **Enregistrer comme modèle**, entrez un nom de fichier et un nom de modèle, activez la case à cocher **Inclure le contenu**, puis cliquez sur **Terminer**.  
  
     Le contenu du site est alors enregistré dans le fichier .wsp.  
  
3.  Après avoir exporté la solution, cliquez sur le lien **Galerie des solutions** pour afficher la liste de fichiers de solutions disponibles.  
  
4.  Ouvrir le menu contextuel du fichier de .wsp, puis choisissez **Enregistrer la cible sous** pour l'enregistrer dans le système.  
  
## Importer des éléments dans Visual Studio  
 Importez le fichier .wsp dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Une fois le contenu importé, vous pouvez le personnaliser, ajouter d'autres d'éléments, puis le déployer.  
  
#### Pour importer des éléments à partir du fichier .wsp dans Visual Studio  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet **Importer le package de solution SharePoint 2010**.  
  
2.  Dans la page **Sélectionner les éléments à importer**, sous **Module**, dans la colonne **Type**, sélectionnez uniquement les cases à cocher des fichiers repris dans le tableau suivant pour l'importation.  
  
    |Nom de fichier|Description|  
    |--------------------|-----------------|  
    |\_catalogsmasterpage\_|Page maître personnalisée.|  
    |images\_|Fichier image dans le système de fichiers SharePoint.|  
    |SitePages\_|Page de site.|  
  
3.  Cliquez sur le bouton **Terminer** pour importer les éléments sélectionnés.  
  
4.  Dans l'**Explorateur de solutions**, cliquez surle noeud \_catalogsmasterpage\_ et affectez la valeur **Automatique** à sa propriété **Résolution de conflit de déploiement**.  
  
     Cela permet de s'assurer que tous les éventuels conflits de déploiement sont résolus automatiquement.  
  
5.  Si votre nouvelle page maître porte le même nom qu'une page existante, assurez\-vous que la page existante n'est pas marquée comme page maître par défaut ou page maître personnalisée dans SharePoint Designer.  
  
     Si une page maître existante est marquée comme page maître par défaut ou page maître personnalisée, vous obtenez une erreur de déploiement qui indique que la page maître ne peut pas être supprimée.  Pour éviter ce problème, procédez comme suit :  
  
    -   Si la page maître existante est définie comme page maître par défaut, définissez temporairement une autre page maître comme page maître par défaut.  Après avoir déployé les fichiers sur SharePoint, définissez votre nouvelle page maître comme page maître par défaut.  
  
    -   Si la page maître existante est définie comme page maître personnalisée, définissez temporairement une autre page maître comme page maître personnalisée.  Après avoir déployé les fichiers sur SharePoint, définissez votre nouvelle page maître comme page maître personnalisée.  
  
6.  Dans la barre de menus, choisissez **Générer**, puis **Déployer la solution**.  
  
7.  Ouvrez le site SharePoint pour afficher les éléments déployés.  
  
 Un autre manière d'importer des fichiers dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et de les déployer sur SharePoint consiste à ajouter les fichiers dans des modules dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Comment : importer une page maître ou un thème](../sharepoint/how-to-import-a-master-page-or-theme.md) et [Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Voir aussi  
 [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  