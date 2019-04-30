---
title: 'Procédure pas à pas : Importer des éléments à partir d’un Site SharePoint existant | Microsoft Docs'
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
ms.openlocfilehash: a2727f0f3a5f2b46c5110a33e63b102f9d26bdaf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446612"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Procédure pas à pas : Importer des éléments à partir d’un site SharePoint existant
  Cette procédure pas à pas montre comment importer des éléments à partir d’un site SharePoint existant dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint.

 Cette procédure pas à pas décrit les tâches suivantes :

- Personnalisation d’un site SharePoint en ajoutant une colonne de site personnalisée (également appelé un *champ*.

- Exportation d’un site SharePoint vers un fichier .wsp.

- Importation du fichier .wsp dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint en utilisant le projet d’importation .wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Personnaliser un site SharePoint
 Pour cet exemple, vous créer et personnaliser un sous-site SharePoint en y ajoutant une nouvelle colonne de site et en créant un autre sous-site pour une utilisation ultérieure. Plus tard, vous exporter le premier sous-site vers un fichier .wsp et ensuite importer la colonne de site personnalisé dans le deuxième sous-site en utilisant le projet d’importation .wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Pour créer et personnaliser un site SharePoint

1. Ouvrir un site SharePoint à l’aide d’un navigateur Web, comme http://<em>nom système</em>/SitePages/Home.aspx.

2. Créer un sous-site du site SharePoint principal en ouvrant le **Actions du Site** menu, puis en choisissant **nouveau Site**.

3. Dans le site **créer** boîte de dialogue, sélectionnez le **Site vide** type.

4. Dans le **titre** , entrez **Site colonne Test 1**; dans le **nom de l’URL** , entrez **TestColonne1**; laissez les autres paramètres par défaut valeurs ; puis choisissez le **créer** bouton.

5. Une fois le site est créé, accédez dans le navigateur vers le site principal, http://<em>nom système</em>/SitePages/Home.aspx.

6. Là encore, créez un sous-site vide hors du site SharePoint principal en ouvrant le **Actions du Site** menu, en choisissant **nouveau Site**, puis en choisissant le **Site vide** type.

7. Dans le **titre** , entrez **Site colonne Test 2**; dans le **nom de l’URL** , entrez **TestColonne2**; laissez les autres paramètres par défaut valeurs ; puis choisissez le **créer** bouton.

8. Revenez à la première sous-site, http://<em>Nom_système</em>/columntest1/default.aspx.

9. Sur le **Actions du Site** menu, choisissez **paramètres du Site** pour afficher la page Paramètres du Site.

10. Dans le **galeries** , choisissez le **colonnes de Site** lien.

11. En haut de la **galerie des colonnes de Site** page, choisissez le **créer** bouton.

12. Dans le **nom de colonne** , entrez **colonne Test**, conservez les autres valeurs par défaut, puis choisissez le **OK** bouton.

13. Le **colonne Test** s’affiche sous les colonnes personnalisées titre dans la galerie des colonnes de Site.

## <a name="exporting-the-sharepoint-site"></a>Exportation du site SharePoint
 Ensuite, obtenez un fichier de configuration (.wsp) SharePoint qui contient les éléments de SharePoint et les éléments que vous souhaitez importer dans votre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet SharePoint. Si vous n’avez pas déjà d’un fichier .wsp, vous devez créer un à partir d’un site SharePoint existant. Pour cet exemple, vous allez exporter le site SharePoint par défaut dans un fichier .wsp.

> [!IMPORTANT]
> Si vous recevez une erreur d’exécution la procédure suivante, vous devez effectuer la procédure sur un système qui a accès au site SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Pour exporter un site SharePoint existant

1. Dans le site SharePoint, choisissez **paramètres du Site** sur le **Actions du Site** onglet pour afficher la page Paramètres du Site.

2. Dans le **Actions du Site** section de la page Paramètres du Site, choisissez le **site enregistrer en tant que modèle** lien.

3. Dans le **nom de fichier** , entrez **SiteExemple**, puis, dans le **nom du modèle** , entrez **Site exemple**.

4. Pour cet exemple, laissez le **inclure du contenu** case à cocher désactivée.

     Si vous activez cette case, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enregistre toutes les listes et bibliothèques de documents et leur contenu, dans le fichier .wsp. Bien que cela est utile dans certaines circonstances, il n’est pas nécessaire dans cet exemple.

5. Lorsque l’opération se termine correctement, choisissez le **galerie de solutions** lien pour afficher le fichier .wsp.

     Pour afficher la page de la galerie de solutions ultérieure, ouvrez la **Actions du Site** menu, choisissez **paramètres du Site**, choisissez la **accéder aux paramètres du site de niveau supérieur** lien dans la  **Administration de la Collection de sites** section et cliquez sur le **Solutions** lien dans la **galeries** section.

6. Dans la galerie de solutions, choisissez le **SiteExemple** lien.

7. Dans le **téléchargement de fichier** boîte de dialogue, sélectionnez le **enregistrer** bouton pour enregistrer le fichier sur votre système local, par défaut, dans le dossier Téléchargements.

## <a name="import-the-wsp-file"></a>Importez le fichier .wsp
 Maintenant que vous avez un *.wsp* fichier qui contient un élément que vous souhaitez réutiliser (la colonne de site personnalisée colonne Test), importez le *.wsp* fichier pour y accéder.

### <a name="to-import-a-wsp-file"></a>Pour importer un fichier .wsp

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, cliquez sur **fichier** > **nouveau** > **projet** pour afficher la **nouveau projet**boîte de dialogue. Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, dans la barre de menus, choisissez **fichier** > **nouveau projet**.

2. Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.

3. Choisissez le **importer un Package SharePoint 2010 Solution** modèle dans le **modèles** volet, laissez le nom du projet WspImportProject1, puis choisissez le **OK** bouton.

    Le **Assistant Personnalisation de SharePoint** s’affiche.

4. Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] du deuxième sous-site SharePoint que vous avez créé précédemment. Vous allez ajouter la nouvelle personnalisée champ d’élément, http://<em>nom système</em>/columntest2, à ce sous-site.

5. Dans le **quel est le niveau de confiance de cette solution SharePoint ?** section, conservez la sélection en tant que **déployer en tant que sandboxed solution**.

6. Dans le **spécifier la nouvelle source de projet** page, accédez à l’emplacement sur le système où vous avez enregistré le *.wsp* fichier précédemment, puis choisissez le **suivant** bouton.

   > [!NOTE]
   > Si vous choisissez la **Terminer** bouton sur cette page, tous les éléments disponibles dans le *.wsp* fichier sera importé.

7. Dans le **sélectionner les éléments à importer** boîte, désactivez toutes les cases à cocher dans la liste à l’exception de **colonne Test**, puis choisissez le **Terminer** bouton.

    Étant donné que la liste contient de nombreux éléments, vous pouvez choisir le **Ctrl**+**A** clés pour choisir tous les éléments dans la liste, appuyez sur la touche de barre d’espace pour effacer toutes les cases à cocher, puis sélectionnez uniquement la vérification zone située en regard du **colonne Test** élément.

    Une fois l’opération d’importation est terminée, un nouveau projet nommé **WspImportProject1** est créé qui contient un dossier nommé **champs**. Dans ce dossier est la colonne de site personnalisé **colonne Test** et son fichier de définition *Elements.xml*.

## <a name="deploy-the-project"></a>Déployer le projet
 Enfin, déployez **WspImportProject1** sur SharePoint deuxième sous-site que vous avez créé précédemment pour afficher la colonne de site personnalisé.

### <a name="to-deploy-the-project"></a>Pour déployer le projet

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], choisissez le **F5** clé pour déployer et exécuter le *.wsp* importer le projet.

2. Sur le site SharePoint, ouvrez le **Actions du Site** menu, puis choisissez **paramètres du Site** pour afficher la page Paramètres du Site.

3. Dans le **galeries** , choisissez le **colonnes de Site** lien.

4. Faites défiler jusqu'à la **colonnes personnalisées** section.

     Notez que la colonne de site personnalisé que vous avez importé à partir du premier site SharePoint s’affiche dans la liste.

## <a name="see-also"></a>Voir aussi
- [Importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
