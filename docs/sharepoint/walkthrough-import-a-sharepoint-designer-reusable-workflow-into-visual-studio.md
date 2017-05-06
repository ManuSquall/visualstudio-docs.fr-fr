---
title: "Proc&#233;dure pas &#224; pas&#160;: importation d&#39;un flux de travail r&#233;utilisable de SharePoint Designer dans Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, importation de flux de travail réutilisables"
  - "flux de travail réutilisables (développement SharePoint dans Visual Studio)"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Proc&#233;dure pas &#224; pas&#160;: importation d&#39;un flux de travail r&#233;utilisable de SharePoint Designer dans Visual Studio
  Cette procédure pas à pas montre comment importer un flux de travail réutilisable créé avec SharePoint Designer 2010 dans un projet de flux de travail SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Les flux de travail créés sous SharePoint Designer \(ou les *flux de travail déclaratifs*\) se composent d'instructions [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] au lieu de code.  Les *flux de travail réutilisables*, nouveauté de SharePoint Designer 2010, sont des flux de travail déclaratifs portables prévus pour être utilisés par différentes listes sur les sites SharePoint.  
  
 Les flux de travail créés dans [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], tels que les flux de travail séquentiels et les flux de travail de machine à états, sont appelés des *flux de travail avec code*.  Ce type de flux de travail est constitué de fichiers XML et de modules de code dans lesquels les utilisateurs peuvent personnaliser le comportement du flux de travail.  
  
 Visual Studio vous permet d'importer des flux de travail réutilisables créés dans SharePoint Designer 2010 et de les convertir sous forme de flux de travail avec code en vue de les exploiter sur vos sites SharePoint.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'un flux de travail réutilisable simple dans SharePoint Designer.  
  
-   Exportation du flux de travail réutilisable SharePoint Designer dans un fichier .wsp et dans SharePoint.  
  
-   Importation du fichier .wsp dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] au moyen du projet Importer le flux de travail réutilisable.  
  
-   Modification du flux de travail en y ajoutant du code.  
  
-   Utilisation du flux de travail importé dans un site SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et de SharePoint prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## Création de sous\-sites SharePoint cibles  
 Commencez par créer deux nouveaux sous\-sites SharePoint : un pour héberger les flux de travail réutilisables à partir de SharePoint Designer, un autre pour héberger les flux de travail convertis.  
  
#### Pour créer des sous\-sites SharePoint  
  
1.  Dans le concepteur SharePoint 2010, dans la barre de menus, cliquez **Fichier**, **Nouveau site Web vide**.  
  
2.  Dans la boîte de dialogue **Nouveau site Web vide**, naviguez jusqu'au site SharePoint où vous souhaitez créer le flux de travail, ou utilisez la valeur par défaut http:\/\/*SystemName*\/, puis cliquez sur le bouton **OK**.  
  
     La page d'accueil s'affiche.  
  
3.  Dans la section **Sous\-sites**, cliquez sur le bouton **Nouveau**.  
  
4.  Dans la boîte de dialogue **Nouveau**, choisissez **Modèles SharePoint** de la liste dans du volet gauche, puis choisissez **Site d'équipe** dans la liste du volet droit.  
  
5.  Dans la zone **Indiquez l'emplacement du nouveau site Web**, remplacez le mot **sous\-site** dans l'URL par SPD1, puis cliquez sur **OK**.  
  
     Cela a pour effet d'ouvrir le nouveau sous\-site dans SharePoint Designer.  Fermez cette instance de SharePoint Designer et revenez à la première instance \(site de niveau supérieur\).  
  
6.  Répétez les étapes 3 à 5 pour créer le deuxième sous\-site, en remplaçant cette fois le mot **sous\-site** dans l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] par SPD2.  
  
## Création d'un flux de travail réutilisable SharePoint Designer  
 Comme SharePoint n'offre aucun flux de travail réutilisable adapté à cet exemple, vous allez en créer un.  Le principe de ce flux de travail est simple : assigner une tâche à l'utilisateur dès que celui\-ci entrera une nouvelle tâche portant un titre précis dans la liste des tâches.  
  
#### Pour créer un flux de travail réutilisable SharePoint Designer  
  
1.  Dans la section **Sous\-sites**, choisissez le site **SPD1** pour le modifier.  
  
2.  Sur le ruban, cliquez sur le bouton **Flux de travail réutilisable**.  
  
     Cela a pour effet d'ouvrir l'Assistant Flux de travail réutilisable.  
  
3.  Dans la zone **Nom**, entrez Flux de travail des tâches SPD.  
  
4.  Dans la liste **Type de contenu**, choisissez **Tâche**, puis le bouton **OK**.  
  
     Le flux de travail s'ouvre dans le Concepteur de flux de travail SharePoint Designer.  
  
5.  Dans le concepteur de flux de travail, sélectionnez l'étape 1, puis, dans le ruban, sélectionnez le bouton **Condition**.  
  
6.  Dans la liste des conditions, choisissez **Si l'élément du champ courant vaut la valeur**.  
  
     Cette étape ajoute une condition nommée **Si le champ vaut la valeur**.  
  
7.  Dans la condition **Si le champ est égal à la valeur**, choisissez le lien **champ**.  
  
8.  Dans la liste de valeurs, sélectionnez **Titre**.  
  
9. Dans la condition **Si le champ vaut la valeur**, sélectionnez le lien **valeur**.  
  
10. Dans la zone, entrez Nouvelle tâche.  
  
     L'énoncé de la condition est désormais **Si Élément actif:Titre est égal à Nouvelle tâche**.  
  
11. Sélectionnez la ligne dans l'instruction de la condition, puis, dans le ruban, cliquez sur le bouton **Action**.  
  
12. Dans la liste d'actions, choisissez **Définissez le champ de l'élément actuel**.  
  
13. Dans l'action **Définir la valeur du champ**, choisissez le lien **champ**, puis, dans la liste, sélectionnez **Assigné à**.  
  
14. Dans l'action **Définir la valeur du champ**, sélectionnez le lien **valeur**, puis, dans la liste des utilisateurs et groupes existants, choisissez **Utilisateur qui a créé l'élément**.  
  
15. Choisissez le bouton **Ajouter**, puis **OK**.  
  
     L'instruction d'action correspondant maintenant à : **Définir Assigné à à Élément actif:CreatedBy**.  
  
## Enregistrement et déploiement du flux de travail réutilisable  
 Étant donné que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] permet uniquement d'importer des fichiers .wsp, vous devez enregistrer le flux de travail réutilisable sous la forme d'un fichier .wsp et le déployer dans SharePoint avant de l'importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Si une erreur d'exécution s'affiche au cours de la procédure suivante, cela signifie que vous devez exécuter la procédure sur un système ayant accès au site SharePoint.  
  
#### Pour enregistrer et déployer le flux de travail réutilisable  
  
1.  Dans la partie supérieure de SharePoint Designer, cliquez sur le bouton **Enregistrer** pour enregistrer votre progression, puis cliquez sur le bouton **Publier** pour déployer le flux de travail sur le site SharePoint **SPD1**.  
  
2.  Dans le volet de navigation, choisissez l'objet **Flux de travail**.  
  
3.  Sous **Flux de travail réutilisable**, choisissez **Flux de travail de tâches SPD**.  
  
4.  Dans le ruban, cliquez sur le bouton **Enregistrer comme modèle** pour enregistrer le flux de travail sous la forme d'un fichier .wsp.  
  
5.  Ouvrez le site SharePoint **SPD1** dans un navigateur pour afficher le fichier .wsp dans SharePoint.  
  
6.  Dans la barre de démarrage rapide, sélectionnez le lien **Bibliothèques**.  
  
7.  Dans la section **Bibliothèque de documents**, choisissez le lien **Éléments de site**.  
  
     Le fichier **Flux de travail des tâches SPD** apparaît avec d'autres éléments de site.  
  
8.  Dans la liste des fichiers, sélectionnez le nom de ce fichier  
  
9. Cliquez sur le bouton **Enregistrer** dans la boîte de dialogue **Téléchargement de fichier** pour enregistrer le fichier .wsp sur le système.  
  
## Importation du fichier .wsp dans Visual Studio  
 Importez le fichier .wsp dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en utilisant un projet Importer le flux de travail réutilisable.  Ce projet a pour fonction de convertir le flux de travail d'un flux de travail réutilisable déclaratif en un flux de travail avec code.  Une fois la conversion réalisée, vous utiliserez le code pour modifier son comportement.  
  
#### Pour importer un flux de travail à partir d'un fichier .wsp et le modifier  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez le nœud **SharePoint** sous **Visual C\#** ou **Visual Basic**, puis choisissez le nœud **2010**.  
  
3.  Dans le volet **Modèles**, sélectionnez le modèle **Flux de travail Import Reusable SharePoint 2010**, laissez **WorkflowImportProject1** pour le nom du projet, puis cliquez sur le bouton **OK**.  
  
     L'Assistant Personnalisation de SharePoint s'affiche.  
  
4.  Dans la page **Spécifier le site et le niveau de sécurité pour le débogage**, entrez le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] du deuxième sous\-site SharePoint que vous avez créé précédemment : http:\/\/*system name*\/SPD2.  
  
5.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, choisissez la case d'option **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Suivant**.  
  
     Pour plus d'informations sur les différences entre les solutions bac à sable \(sandbox\) et les solutions de batterie, consultez [Considérations sur les solutions bac à sable &#40;sandbox&#41;](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Dans la page **Spécifier la nouvelle source de projet**, accédez à l'emplacement du système où vous avez enregistré le fichier .wsp précédemment, ouvrez le fichier puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Cliquez sur le bouton **Terminer** pour importer tous les éléments disponibles dans le fichier de .wsp.  
  
     Cette opération affiche la liste des flux de travail réutilisables disponibles pour l'importation.  
  
7.  Dans la zone **Sélectionner les éléments à importer**, sélectionnez le flux de travail **Flux de travail des tâches SPD**, puis cliquez sur le bouton **Terminer**.  
  
     Une fois l'opération d'importation terminée, un nouveau projet appelé **WorkflowImportProject1** dans lequel figure un flux de travail nommé **SPD\_Workflow\_TestFT** est alors créé.  Ce dossier contient le fichier de définition du flux de travail \(Elements.xml\) et le fichier du Concepteur de flux de travail \(.xoml\).  Le concepteur contient deux fichiers : le fichier de règles \(.rules\) et le fichier code\-behind \(.cs ou .vb, selon le langage de programmation de votre projet\).  
  
8.  Dans l'**Explorateur de solutions**, supprimez le dossier **Autres fichiers importés**.  
  
9. Dans le fichier Elements.xml, supprimez `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. Dans **Explorateur de solutions**, choisissez **WorkflowImportProject1**, puis, dans la barre de menus, cliquez **Projet**, **Défini comme projet de démarrage** pour définir **WorkflowImportProject1** en tant qu'élément de démarrage.  
  
     Cette opération affiche immédiatement la liste lorsque vous déboguez le projet.  
  
11. Étant donné que le modèle **Importer le flux de travail réutilisable SharePoint 2010** n'importe pas les valeurs de propriété d'association pour le flux de travail importé, vous devez les entrer.  Pour cela :  
  
    1.  Dans l'**Explorateur de solutions**, choisissez le nœud  **Flux de travail SPD TestFT**.  
  
    2.  Cliquez sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\) à côté de l'une des propriétés de liste, telle que la propriété **Liste cible**.  
  
    3.  Remplissez les valeurs manquantes dans l'Assistant de personnalisation SharePoint, puis choisissez le bouton **Terminer**.  
  
12. Choisissez le fichier .xoml, puis, dans la barre de menus, cliquez sur **Affichage**, **Concepteur** pour afficher le flux de travail importé dans le concepteur de flux de travail.  
  
13. Dans le nœud **Windows v3.0 travail** de la **Boîte à outils**, effectuez l'une des étapes suivantes.  
  
    -   Ouvrez le menu contextuel de l'activité **Code**, puis choisissez **Copier**.  Dans le concepteur de flux de travail, ouvrez le menu contextuel de la ligne dans l'activité **SequenceActivity1**, puis choisissez **Coller**.  
  
    -   Faites glisser l'activité **Code** depuis la **Boîte à outils** vers le concepteur de flux de travail, et connectez\-la à la ligne dans l'activité **SequenceActivity1**.  
  
     Vous venez d'ajouter une activité nommée **CodeActivity1** dans le Concepteur de flux de travail.  Vous allez maintenant y ajouter une action de code destinée à créer une annonce dans la liste Annonces au lancement du flux de travail par l'utilisateur.  
  
14. Effectuez l'un des ensembles d'étapes suivants :  
  
    -   Double\-cliquez sur **CodeActivity1** pour générer un gestionnaire d'événements et consulter le code.  
  
    -   Dans la fenêtre **Propriétés** pour **CodeActivity1**, affectez la valeur de la propriété **ExecuteCode** à **codeActivity\_ExecuteCode**.  
  
15. Ajoutez ce qui suit sous les instructions **using** ou **Imports** existantes :  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Remplacez `codeActivity1_ExecuteCode` par ce qui suit :  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## Déploiement du projet et association du flux de travail  
 Exécutez WorkflowImportProject1 pour le déployer sur un site SharePoint, puis associez le flux de travail à la liste des tâches afin d'afficher et de tester le flux de travail modifié après conversion.  
  
#### Pour déployer le projet et associer le flux de travail  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], appuyez surla touche F5 pour exécuter et déployer le projet de flux de travail converti.  
  
2.  Dans la barre de lancement rapide, cliquez sur le lien **Tâches** pour afficher la liste des tâches.  
  
3.  Sous l'onglet **Répertorier les outils**, cliquez sur le bouton **Éléments**, puis cliquez sur le bouton **Nouvel élément**.  
  
     La boîte de dialogue **Tâches \- Nouvel élément** s'ouvre.  
  
4.  Dans la zone **Titre**, entrez Nouvelle tâche, puis choisissez le bouton **Enregistrer**.  
  
5.  Sous l'onglet **Liste d'outils**, cliquez sur le bouton **Liste**, puis cliquez sur le bouton **Paramètres du pool**.  
  
     La page **Liste des paramètres** s'affiche.  
  
6.  dans la section **Autorisations et gestion**, cliquez sur le lien **Paramètres du flux de travail**.  
  
     La page **Paramètres de flux de travail** s'affiche.  
  
7.  Sélectionnez le lien **Ajouter un flux de travail**.  
  
8.  Dans la liste **Flux de travail**, sélectionnez **WorkflowImportProject1 \- Test du flux de travail SPD**.  
  
9. Dans la zone de texte **Nom**, entrez SPD Workflow Test puis choisissez le bouton **OK**.  
  
10. Dans la barre de lancement rapide, choisissez la liste **Tâches**.  
  
11. Cliquez sur la flèche à côté de **Nouvelle tâche**, puis, dans la liste, sélectionnez **Flux de travail**.  
  
12. Dans la section **Commencer un nouveau flux de travail**, choisissez le lien **Test SPD de flux de travail**, puis cliquez sur le bouton **Start** pour initialiser le flux de travail.  
  
    > [!NOTE]  
    >  Il est possible sinon d'associer automatiquement un flux de travail à une liste en exécutant l'Assistant de paramétrage du flux de travail et en configurant le flux de travail à cet effet.  
  
     Deux actions sont exécutées par le flux de travail : votre nom apparaît dans la colonne **Assigné à** de la tâche et une annonce s'affiche dans la liste **Annonces**.  
  
## Voir aussi  
 [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Création de contrôles réutilisables pour les composants WebPart ou les pages d'application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  