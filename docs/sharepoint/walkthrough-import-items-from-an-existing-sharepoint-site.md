---
title: "Proc&#233;dure pas &#224; pas&#160;: importation d&#39;&#233;l&#233;ments d&#39;un site SharePoint existant"
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
  - "importer des éléments (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, importer des éléments"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Proc&#233;dure pas &#224; pas&#160;: importation d&#39;&#233;l&#233;ments d&#39;un site SharePoint existant
  Cette procédure pas à pas montre comment importer des éléments à partir d'un site SharePoint existant dans un projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Personnalisation d'un site SharePoint en ajoutant une colonne de site personnalisée \(également appelé un *champ*\).  
  
-   Exportation d'un site SharePoint vers un fichier .wsp.  
  
-   Importation du fichier .wsp dans SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] par l'intermédiaire du projet d'importation .wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et de SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Personnalisation d'un site SharePoint  
 Dans cet exemple, vous serez amené à concevoir et à personnaliser un sous\-site SharePoint en y incorporant une nouvelle colonne de site, puis en créant un autre sous\-site en vue d'une utilisation ultérieure.  Vous serez chargé ensuite d'exporter le premier sous\-site vers un fichier .wsp, puis d'importer la colonne de site personnalisée dans le deuxième sous\-site par l'intermédiaire du projet d'importation .wsp.  
  
#### Pour concevoir et personnaliser un site SharePoint  
  
1.  Ouvrez un site SharePoint dans un navigateur Web, comme par exemple http:\/\/*system name*\/SitePages\/Home.aspx.  
  
2.  Créez un sous\-site hors du site SharePoint principal en ouvrant le menu **Actions du site** puis en cliquant sur **Nouveau site**.  
  
3.  Dans la boîte de dialogue **Créer** du site, choisissez le type **Site vide**.  
  
4.  Dans la zone **Titre**, entrez Test de la colonne de site 1, dans la zone **Nom d'URL**, tapez TestColonne1, conservez les autres paramètres par défaut, puis cliquez sur le bouton **Créer**.  
  
5.  Après avoir créé le site, revenez au site principal \(http:\/\/*system name*\/SitePages\/Home.aspx\) dans le navigateur Web.  
  
6.  Créez à nouveau un sous\-site vide hors du site SharePoint principal en ouvrant le menu **Actions du site**, puis en choisissant**Nouveau site**, et **Site vide**.  
  
7.  Dans la zone **Titre**, entrez Test de la colonne de site 2, dans la zone **Nom d'URL**, tapez TestColonne2, conservez les autres paramètres par défaut, puis cliquez sur le bouton **Créer**.  
  
8.  Accédez au premier signet sous\-site, http:\/\/*SystemName*\/columntest1\/default.aspx.  
  
9. Dans le menu **Actions du site**, choisissez **Paramètres du site** pour afficher la page Paramètres du site.  
  
10. Dans la section **Galeries**, cliquez sur le lien **Colonnes de site**.  
  
11. En haut de la page **Galerie des colonnes de sites**, cliquez sur le bouton **Créer**.  
  
12. Dans la zone **Nom de la colonne**, entrez la colonne de test, conservez les autres valeurs par défaut, puis cliquez sur le bouton **OK**.  
  
13. La **Colonne test** s'affiche sous l'en\-tête Colonnes personnalisées dans la galerie des colonnes de sites.  
  
## Exportation du site SharePoint  
 Vous avez besoin, à présent, d'un fichier d'installation SharePoint \(.wsp\) dans lequel figurent les éléments SharePoint à importer dans votre projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Si vous ne disposez d'aucun fichier .wsp, vous devez alors en créer un à partir d'un site SharePoint existant.  Cet exemple suppose que vous exportiez le site SharePoint par défaut dans un fichier .wsp.  
  
> [!IMPORTANT]  
>  Si une erreur d'exécution s'affiche au cours de la procédure suivante, cela signifie que vous devez exécuter la procédure sur un système ayant accès au site SharePoint.  
  
#### Pour exporter un site SharePoint existant  
  
1.  Sous SharePoint, cliquez sur **Paramètres du site** dans l'onglet **Actions du site** afin d'afficher la page Paramètres du site.  
  
2.  Dans la section **Actions du site** de la page Paramètres du site, cliquez sur le lien **Enregistrer le site en tant que modèle**.  
  
3.  Dans la zone **Nom de fichier**, tapez SiteExemple, et dans la zone **Nom du modèle**, tapez Site exemple.  
  
4.  Dans cet exemple, n'activez pas la case à cocher **Inclure le contenu**.  
  
     Si vous activez cette option, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enregistre toutes les listes et bibliothèques de documents, ainsi que leur contenu, dans le fichier .wsp.  Si cela présente un intérêt dans certaines circonstances, cela n'est pas le cas ici.  
  
5.  Une fois l'opération d'exportation terminée, cliquez sur le lien **galerie des solutions** pour consulter le fichier .wsp.  
  
     Pour afficher la page de la galerie des solutions par la suite, ouvrez le menu **Actions du site** dans l'onglet **Paramètres du site**, cliquez sur **Accéder aux paramètres du site de niveau supérieur** dans la section **Administration de la collection de sites**, puis sur le lien **Solutions** dans la section **Galeries**.  
  
6.  Dans la galerie de solutions, sélectionnez le lien **ExampleSite**.  
  
7.  Dans la boîte de dialogue **Téléchargement de fichier**, cliquez sur le bouton **Enregistrer** pour enregistrer le fichier sur votre système local, par défaut, dans le dossier téléchargements.  
  
## Importation du fichier .wsp  
 Pour accéder au fichier .wsp contenant l'élément que vous avez l'intention de réutiliser \(c'est\-à\-dire la colonne de site personnalisée Colonne test\), il convient d'importer ce fichier.  
  
#### Pour importer un fichier .wsp  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour afficher la boîte de dialogue **Nouveau projet**.  Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, dans la barre de menu cliquez sur **Fichier**, puis **Nouveau Projet**.  
  
2.  Développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis cliquez sur le noeud **2010**.  
  
3.  Choisissez le modèle **Importer le package de solution SharePoint 2010** dans le volet **Modèles**, conservez le nom du projet WspImportProject1, puis cliquez sur **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  
  
4.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] du deuxième sous\-site SharePoint que vous avez créé précédemment.  Vous allez ajouter un nouvel élément personnalisé de champ, http:\/\/*system name*\/columntest2, sur le sous\-site.  
  
5.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, conservez l'option sélectionnée **Déployer en tant que solution bac à sable \(sandbox\)**.  
  
6.  Dans la page **Spécifier la nouvelle source de projet**, accédez à l'emplacement du système où vous avez précédemment enregistré le fichier .wsp, puis cliquez sur le bouton **Suivant**.  
  
    > [!NOTE]  
    >  Si vous choisissez le bouton **Terminer** de cette page, tous les éléments disponibles dans le fichier de .wsp sont importés.  
  
7.  Dans la zone **Sélectionner les éléments à importer**, retirez tous les cases à cocher de la liste à l'exception de **Colonne test**, puis cliquez sur **Terminer**.  
  
     Étant donné que la liste contient de nombreux éléments, vous pouvez appuyer les touches CTRL \+ A pour sélectionner tous les éléments dans la liste, vous pouvez appuyer sur la touche Espace pour désactiver toutes les cases à cocher, puis sélectionner uniquement la case à côté de l'élément **Colonne Test**.  
  
     Une fois l'opération d'importation terminée, un nouveau projet appelé **WspImportProject1** dans lequel figure un dossier nommé **Champs** est alors créé.  Ce dossier contient la colonne de site personnalisée \(**Colonne test**\) ainsi que son fichier de définition Elements.xml.  
  
## Déploiement du projet  
 La dernière étape consiste à déployer **WspImportProject1** sur le deuxième sous\-site SharePoint que vous avez créé précédemment pour afficher la colonne de site personnalisée.  
  
#### Pour déployer le projet  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], appuyez sur F5 pour déployer et exécuter le projet d'importation .wsp.  
  
2.  Sur le site SharePoint, ouvrez le menu **Les actions de site**, puis choisissez **Paramètres du site** pour afficher la page paramètres du site.  
  
3.  Dans la section **Galeries**, cliquez sur le lien **Colonnes de site**.  
  
4.  Faites défiler l'écran vers le bas jusqu'à la section **Colonnes personnalisées**.  
  
     La colonne de site personnalisée que vous avez importée à partir du premier site SharePoint figure, à présent, dans la liste.  
  
## Voir aussi  
 [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  