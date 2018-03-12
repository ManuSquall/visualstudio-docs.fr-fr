---
title: "Procédure pas à pas : Importer des éléments à partir d’un Site SharePoint existant | Documents Microsoft"
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b9d1bcc72bd22e7c528b2a3d8752d15b7005fea5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procédure pas à pas : importation d'éléments d'un site SharePoint existant
  Cette procédure pas à pas montre comment importer des éléments à partir d’un site SharePoint existant vers un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Personnalisation d’un site SharePoint en ajoutant une colonne de site personnalisée (également appelé un *champ*.  
  
-   Exportation d’un site SharePoint vers un fichier .wsp.  
  
-   Importation du fichier .wsp dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint en utilisant le projet d’importation .wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="customizing-a-sharepoint-site"></a>Personnalisation d’un Site SharePoint  
 Pour cet exemple, vous créez et personnaliser un sous-site SharePoint en y ajoutant une nouvelle colonne de site et en créant un autre sous-site pour une utilisation ultérieure. Une version ultérieure, vous exportez le premier sous-site vers un fichier .wsp et puis importer la colonne de site personnalisée dans le deuxième sous-site en utilisant le projet d’importation .wsp.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Pour créer et personnaliser un site SharePoint  
  
1.  Ouvrir un site SharePoint à l’aide d’un navigateur Web, tel que http://*nom système*/SitePages/Home.aspx.  
  
2.  Créer un sous-site du site SharePoint principal en ouvrant le **Actions du Site** menu, puis en choisissant **nouveau Site**.  
  
3.  Dans la table **créer** boîte de dialogue, choisissez le **Site vide** type.  
  
4.  Dans le **titre** , entrez **Site colonne Test 1**; dans le **nom de l’URL** , entrez **TestColonne1**; conservez les autres paramètres par défaut valeurs ; puis choisissez le **créer** bouton.  
  
5.  Une fois que le site est créé, naviguer dans le navigateur sur le site principal, http://*nom système*/SitePages/Home.aspx.  
  
6.  Là encore, créez un sous-site vide hors du site SharePoint principal en ouvrant le **Actions du Site** menu, en choisissant **nouveau Site**, puis en choisissant le **Site vide** type.  
  
7.  Dans le **titre** , entrez **Site colonne Test 2**; dans le **nom de l’URL** , entrez **TestColonne2**; laissez les autres paramètres par défaut valeurs ; puis choisissez le **créer** bouton.  
  
8.  Revenez à la première sous-site, http://*Nom_système*/columntest1/default.aspx.  
  
9. Sur le **Actions du Site** menu, choisissez **paramètres du Site** pour afficher la page Paramètres du Site.  
  
10. Dans le **galeries** , choisissez le **colonnes de Site** lien.  
  
11. En haut de la **galerie des colonnes de Site** page, choisissez la **créer** bouton.  
  
12. Dans le **nom de la colonne** , entrez **colonne Test**, gardez les autres valeurs par défaut, puis choisissez le **OK** bouton.  
  
13. Le **colonne Test** s’affiche sous les colonnes personnalisées titre dans la galerie des colonnes de Site.  
  
## <a name="exporting-the-sharepoint-site"></a>Exportation du Site SharePoint  
 Ensuite, obtenir un fichier de configuration (.wsp) SharePoint qui contient les éléments de SharePoint et que vous souhaitez importer dans votre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint. Si vous n’avez pas déjà un fichier .wsp, vous devez créer une à partir d’un site SharePoint existant. Pour cet exemple, vous allez exporter le site SharePoint par défaut dans un fichier .wsp.  
  
> [!IMPORTANT]  
>  Si vous recevez une erreur d’exécution de la procédure suivante, vous devez exécuter la procédure sur un système qui a accès au site SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Pour exporter un site SharePoint existant  
  
1.  Dans le site SharePoint, choisissez **paramètres du Site** sur la **Actions du Site** onglet pour afficher la page Paramètres du Site.  
  
2.  Dans le **Actions du Site** section de la page Paramètres du Site, sélectionnez le **site enregistrer en tant que modèle** lien.  
  
3.  Dans le **nom de fichier** , entrez **SiteExemple**et dans le **nom du modèle** , entrez **exemple Site**.  
  
4.  Pour cet exemple, laissez le **inclure du contenu** case à cocher.  
  
     Si vous activez cette case, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enregistre toutes les listes et bibliothèques de documents et leur contenu, dans le fichier .wsp. Bien que cela est utile dans certaines circonstances, il n’est pas requis pour cet exemple.  
  
5.  Lorsque l’opération est terminée, choisissez le **galerie de solutions** lien pour afficher le fichier .wsp.  
  
     Pour afficher la page de la galerie de solutions ultérieure, ouvrez le **Actions du Site** menu, choisissez **paramètres du Site**, choisissez le **accéder aux paramètres du site de niveau supérieur** lien dans le  **Site d’Administration de la Collection** section, puis choisissez le **Solutions** lien dans le **galeries** section.  
  
6.  Dans la galerie de solutions, sélectionnez le **SiteExemple** lien.  
  
7.  Dans le **télécharger le fichier** boîte de dialogue, choisissez le **enregistrer** bouton pour enregistrer le fichier sur votre système local, par défaut, dans le dossier Téléchargements.  
  
## <a name="importing-the-wsp-file"></a>L’importation du fichier .wsp  
 Maintenant que vous avez un fichier .wsp contient un élément que vous souhaitez réutiliser (la colonne de site personnalisée colonne Test), importez le fichier .wsp pour y accéder.  
  
#### <a name="to-import-a-wsp-file"></a>Pour importer un fichier .wsp  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, choisissez **fichier**, **nouveau**, **projet** pour afficher les **nouveau projet** boîte de dialogue. Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, dans la barre de menus, choisissez **fichier**, **nouveau projet**.  
  
2.  Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.  
  
3.  Choisissez le **importer un Package SharePoint 2010 Solution** modèle dans le **modèles** volet, conservez le nom du projet WspImportProject1, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
4.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** , entrez la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] du deuxième sous-site SharePoint que vous avez créé précédemment. Vous allez ajouter la personnalisée champ d’élément, http://*nom système*/columntest2, à ce sous-site.  
  
5.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** section, conservez la sélection en tant que **déployer comme une solution bac à sable**.  
  
6.  Dans le **spécifier la nouvelle source de projet** page, accédez à l’emplacement sur le système où vous avez enregistré le fichier .wsp précédemment, puis choisissez le **suivant** bouton.  
  
    > [!NOTE]  
    >  Si vous choisissez la **Terminer** bouton sur cette page, tous les éléments disponibles dans le fichier .wsp est importée.  
  
7.  Dans le **sélectionner les éléments à importer** zone, désactivez toutes les cases à cocher dans la liste à l’exception de **colonne Test**, puis choisissez le **Terminer** bouton.  
  
     Étant donné que la liste contient de nombreux éléments, vous pouvez choisir le touches Ctrl + un choisir tous les éléments dans la liste, choisissez la touche espace pour effacer toutes les cases à cocher, puis sélectionnez uniquement la case à cocher à côté du **colonne Test** élément.  
  
     Une fois l’opération d’importation terminée, un nouveau projet nommé **WspImportProject1** est créé qui contient un dossier nommé **champs**. Ce dossier contient la colonne de site personnalisée **colonne Test** et son fichier de définition Elements.xml.  
  
## <a name="deploying-the-project"></a>Déploiement du projet  
 Enfin, déployer **WspImportProject1** sur le deuxième SharePoint sous-site que vous avez créé précédemment pour afficher la colonne de site personnalisée.  
  
#### <a name="to-deploy-the-project"></a>Pour déployer le projet  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], appuyez sur la touche F5 pour déployer et exécuter le projet d’importation .wsp.  
  
2.  Sur le site SharePoint, ouvrez le **Actions du Site** menu, puis choisissez **paramètres du Site** pour afficher la page Paramètres du Site.  
  
3.  Dans le **galeries** , choisissez le **colonnes de Site** lien.  
  
4.  Faites défiler jusqu'à la **colonnes personnalisées** section.  
  
     Notez que la colonne de site personnalisée que vous avez importé à partir du premier site SharePoint s’affiche dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Importation d’éléments d’un Site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  