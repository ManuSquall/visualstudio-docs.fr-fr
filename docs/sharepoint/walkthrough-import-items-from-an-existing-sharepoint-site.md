---
title: 'Procédure pas à pas : importer des éléments à partir d’un site SharePoint existant | Microsoft Docs'
titleSuffix: ''
description: Dans cette procédure pas à pas, importez des éléments d’un site SharePoint existant dans un projet Visual Studio SharePoint.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 861b6ff20f9ceb73c279e54fa89ee513389b6b91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900958"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procédure pas à pas : importer des éléments à partir d’un site SharePoint existant
  Cette procédure pas à pas montre comment importer des éléments à partir d’un site SharePoint existant dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.

 Cette procédure pas à pas décrit les tâches suivantes :

- Personnalisation d’un site SharePoint en ajoutant une colonne de site personnalisée (également appelée *champ*.

- Exportation d’un site SharePoint vers un fichier. wsp.

- Importation du fichier. wsp dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint à l’aide du projet d’importation. wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Personnaliser un site SharePoint
 Pour cet exemple, vous allez créer et personnaliser un sous-site SharePoint en y ajoutant une nouvelle colonne de site et en créant un autre sous-site pour une utilisation ultérieure. Plus tard, vous allez exporter le premier sous-site vers un fichier. wsp, puis importer la colonne de site personnalisée dans le deuxième sous-site à l’aide du projet d’importation. wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Pour créer et personnaliser un site SharePoint

1. Ouvrez un site SharePoint à l’aide d’un navigateur Web, tel que http://<em>System Name</em>/SitePages/Home.aspx.

2. Créez un sous-site à partir du site SharePoint principal en ouvrant le menu **actions du site** , puis en choisissant **nouveau site**.

3. Dans la boîte de dialogue **créer** du site, choisissez le type de **site vide** .

4. Dans la zone **titre** , entrez **test de la colonne de site 1**; dans la zone nom de l' **URL** , entrez **columntest1**; conserver les valeurs par défaut des autres paramètres ; puis cliquez sur le bouton **créer** .

5. Une fois le site créé, accédez de nouveau au site principal à partir du navigateur, http://<em>nom système</em>/SitePages/Home.aspx.

6. Là encore, créez un sous-site vide à partir du site SharePoint principal en ouvrant le menu **actions du site** , en choisissant **nouveau site**, puis en choisissant le type de **site vide** .

7. Dans la zone **titre** , entrez **test de la colonne de site 2**; dans la zone nom de l' **URL** , entrez **columntest2**; conserver les valeurs par défaut des autres paramètres ; puis cliquez sur le bouton **créer** .

8. Revenez au premier sous-site, http://<em>SystemName</em>/columntest1/default.aspx.

9. Dans le menu **actions du site** , choisissez **paramètres** du site pour afficher la page Paramètres du site.

10. Dans la section **galeries** , choisissez le lien **colonnes de site** .

11. En haut de la page **Galerie des colonnes de site** , cliquez sur le bouton **créer** .

12. Dans la zone nom de la **colonne** , entrez **test colonne**, conservez les autres valeurs par défaut, puis choisissez le bouton **OK** .

13. La colonne **colonne de test** s’affiche sous l’en-tête colonnes personnalisées dans la Galerie des colonnes de site.

## <a name="exporting-the-sharepoint-site"></a>Exportation du site SharePoint
 Ensuite, obtenez un fichier d’installation SharePoint (. wsp) qui contient les éléments et éléments SharePoint que vous souhaitez importer dans votre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint. Si vous n’avez pas encore de fichier. wsp, vous devez en créer un à partir d’un site SharePoint existant. Pour cet exemple, vous allez exporter le site SharePoint par défaut dans un fichier. wsp.

> [!IMPORTANT]
> Si vous recevez une erreur d’exécution lors de l’exécution de la procédure suivante, vous devez effectuer la procédure sur un système qui a accès au site SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Pour exporter un site SharePoint existant

1. Sur le site SharePoint, choisissez **paramètres du site** sous l’onglet **actions du site** pour afficher la page Paramètres du site.

2. Dans la section **actions du site** de la page Paramètres du site, choisissez le lien enregistrer le **site en tant que modèle** .

3. Dans la **zone nom de fichier** , entrez **ExampleSite**, puis dans la zone Nom du **modèle** , entrez exemple de **site**.

4. Pour cet exemple, laissez la case à cocher **inclure le contenu** désactivée.

     Si vous activez cette case à cocher, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enregistre toutes les listes et bibliothèques de documents, ainsi que leur contenu, dans le fichier. wsp. Bien que cela soit utile dans certains cas, cela n’est pas obligatoire pour cet exemple.

5. Lorsque l’opération se termine avec succès, cliquez sur le lien de la **Galerie de solutions** pour afficher le fichier. wsp.

     Pour afficher la page de la Galerie de solutions plus tard, ouvrez le menu **actions du site** , choisissez **paramètres du site**, choisissez le lien **accéder aux paramètres de site de niveau supérieur** dans la section Administration de la **collection de sites** , puis cliquez sur le lien **solutions** dans la section **galeries** .

6. Dans la Galerie de solutions, choisissez le lien **ExampleSite** .

7. Dans la boîte de dialogue **téléchargement de fichier** , choisissez le bouton **Enregistrer** pour enregistrer le fichier sur votre système local, par défaut, dans votre dossier téléchargements.

## <a name="import-the-wsp-file"></a>Importer le fichier. wsp
 Maintenant que vous avez un fichier *. wsp* qui contient un élément que vous souhaitez réutiliser (colonne de test de colonne de site personnalisée), importez le fichier *. wsp* pour y accéder.

### <a name="to-import-a-wsp-file"></a>Pour importer un fichier. wsp

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue **nouveau projet** . Si votre IDE est configuré pour utiliser Visual Basic paramètres de développement, dans la barre de menus, choisissez **fichier**  >  **nouveau projet**.

2. Développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Choisissez le modèle **importer le package de solution SharePoint 2010** dans le volet **modèles** , laissez le nom du projet WspImportProject1, puis choisissez le bouton **OK** .

    L' **Assistant Personnalisation de SharePoint** s’affiche.

4. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , entrez le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pour le deuxième sous-site SharePoint que vous avez créé précédemment. Vous allez ajouter le nouvel élément de champ personnalisé, http://<em>System Name</em>/columntest2, à ce sous-site.

5. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , laissez la sélection **déployer en tant que solution bac à sable (sandbox)**.

6. Dans la page **spécifier la nouvelle source du projet** , accédez à l’emplacement sur le système où vous avez enregistré le fichier *. wsp* précédemment, puis cliquez sur le bouton **suivant** .

   > [!NOTE]
   > Si vous choisissez le bouton **Terminer** sur cette page, tous les éléments disponibles dans le fichier *. wsp* seront importés.

7. Dans la zone **Sélectionner les éléments à importer** , désactivez toutes les cases à cocher de la liste à l’exception de la **colonne test**, puis choisissez le bouton **Terminer** .

    Étant donné que la liste contient de nombreux éléments, vous pouvez choisir la touche **CTRL** + **A** pour sélectionner tous les éléments dans la liste, choisir la touche espace pour désactiver toutes les cases à cocher, puis sélectionner uniquement la case à cocher en regard de l’élément de **colonne de test** .

    Une fois l’opération d’importation terminée, un nouveau projet nommé **WspImportProject1** est créé et contient un dossier nommé **Fields**. Dans ce dossier se trouve la colonne de **test** colonne de site personnalisée et son fichier de définition *Elements.xml*.

## <a name="deploy-the-project"></a>Déployer le projet
 Enfin, déployez **WspImportProject1** sur le deuxième sous-site SharePoint que vous avez créé précédemment pour afficher la colonne de site personnalisée.

### <a name="to-deploy-the-project"></a>Pour déployer le projet

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , appuyez sur la touche **F5** pour déployer et exécuter le projet d’importation *. wsp* .

2. Sur le site SharePoint, ouvrez le menu **actions du site** , puis choisissez **paramètres du site** pour afficher la page Paramètres du site.

3. Dans la section **galeries** , choisissez le lien **colonnes de site** .

4. Faites défiler jusqu’à la section **colonnes personnalisées** .

     Notez que la colonne de site personnalisée que vous avez importée à partir du premier site SharePoint apparaît dans la liste.

## <a name="see-also"></a>Voir aussi
- [Importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
