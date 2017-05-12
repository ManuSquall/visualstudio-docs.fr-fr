---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un composant WebPart pour SharePoint &#224; l&#39;aide d&#39;un concepteur"
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
  - "WebParts (développement SharePoint dans Visual Studio), créer"
  - "WebParts (développement SharePoint dans Visual Studio), concepteur"
  - "WebParts (développement SharePoint dans Visual Studio), concevoir"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un composant WebPart pour SharePoint &#224; l&#39;aide d&#39;un concepteur
  Si vous créez des composants WebPart pour un site SharePoint, vos utilisateurs peuvent modifier directement le contenu, l'apparence et le comportement des pages de ce site à l'aide d'un navigateur.  Cette procédure pas à pas vous indique comment créer visuellement un composant WebPart à l'aide d'un modèle de projet **Composant Visual Web Part** SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Le composant WebPart que vous créerez affiche un calendrier mensuel et une case à cocher pour chaque liste de calendriers sur le site.  Les utilisateurs peuvent spécifier les listes de calendriers à inclure dans l'affichage de calendrier mensuel en activant les cases à cocher correspondantes.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un composant WebPart à l'aide du modèle de projet **Composant Visual Web Part**.  
  
-   Conception du composant WebPart à l'aide du concepteur Visual Web Developer dans Visual Studio.  
  
-   Ajout de code pour gérer les événements de contrôles sur le composant WebPart.  
  
-   Test du composant WebPart dans SharePoint.  
  
    > [!NOTE]  
    >  Votre ordinateur peut afficher des noms ou des emplacements différents pour certains éléments de l'interface utilisateur de Visual Studio dans les instructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint.  Consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] ou une version ultérieure.  
  
## Création d'un projet de composant WebPart  
 Commencez par créer un projet de composant WebPart à l'aide du modèle de projet **Composant Visual Web Part**.  
  
#### Pour créer un projet de composant Visual Web Part  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sélectionnant l'option **Exécuter en tant qu'administrateur**.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, sous **Visual C\#** ou **Visual Basic**, développez **Office\/SharePoint**, puis choisissez la catégorie **Solutions SharePoint**.  
  
4.  Dans la liste des modèles, sélectionnez le modèle **SharePoint 2013 \- Composant Visual Web Part**, puis choisissez le bouton **OK**.  
  
     L'**Assistant Personnalisation de SharePoint** s'affiche.  En utilisant cet Assistant, vous pouvez sélectionner le site à utiliser pour déboguer le projet et le niveau de confiance de la solution.  
  
5.  Dans la section **Quel est le niveau de confiance de cette solution SharePoint ?**, choisissez la case d'option **Déployer en tant que solution de batterie**.  
  
6.  Cliquez sur le bouton **Terminer** pour accepter le site SharePoint local par défaut.  
  
## Conception du composant WebPart  
 Concevez le composant WebPart en ajoutant des contrôles de la **Boîte à outils** à la surface du Concepteur Visual Web Developer.  
  
#### Pour concevoir la disposition du composant WebPart  
  
1.  Dans le concepteur Visual Web Developer, choisissez l'onglet **Design** pour passer en mode Design.  
  
2.  Dans la barre de menus, choisissez **Affichage**, **Boîte à outils**.  
  
3.  Dans le nœud **StandardBoîte à outils**, sélectionnez le contrôle **CheckBoxList**, puis effectuez l'une des opérations suivantes :  
  
    -   Ouvrez le menu contextuel du contrôle **CheckBoxList**, choisissez **Copier**, ouvrez le menu contextuel de la première ligne dans le concepteur, puis choisissez **Coller**.  
  
    -   Faites glisser le contrôle **CheckBoxList** de la **Boîte à outils**, puis connectez\-le à la première ligne du concepteur.  
  
4.  Répétez l'étape précédente, mais déplacez un bouton à la ligne suivante du concepteur.  
  
5.  Dans le concepteur, choisissez sur le bouton **Button1**.  
  
6.  Dans la barre de menus, choisissez **Affichage**, **Fenêtre Propriétés**.  
  
     Cela a pour effet d'ouvrir la fenêtre **Propriétés**.  
  
7.  Dans la propriété **Texte** du bouton, entrez Mettre à jour.  
  
## Gestion des événements de contrôles sur le composant WebPart  
 Vous pouvez ajouter du code pour que l'utilisateur puisse ajouter des calendriers à l'affichage de calendrier principal.  
  
#### Pour gérer les événements de contrôles sur le composant WebPart  
  
1.  Effectuez l'un des ensembles d'étapes suivants :  
  
    -   Dans le concepteur, double\-cliquez sur le bouton **Mettre à jour**.  
  
    -   Dans la fenêtre **Propriétés** du bouton **Mise à jour**, choisissez le bouton **Événements**.  Dans la propriété **Click**, entrez **Button1\_Click**, puis choisissez la touche Entrée.  
  
     Le fichier de code du contrôle utilisateur s'ouvre dans l'Éditeur de code et le gestionnaire d'événements `Button1_Click` s'affiche.  Vous ajouterez par la suite du code à ce gestionnaire d'événements.  
  
2.  Ajoutez les instructions suivantes au début du fichier de code du contrôle utilisateur.  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  Ajoutez la ligne de code suivante à la classe `VisualWebPart1`.  Ce code déclare un contrôle d'affichage de calendrier mensuel.  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  Remplacez la méthode `Page_Load` de la classe `VisualWebPart1` par le code suivant.  Ce code exécute les tâches suivantes :  
  
    -   Il ajoute un affichage de calendrier mensuel au contrôle utilisateur.  
  
    -   Il ajoute une case à cocher pour chaque liste de calendriers sur le site.  
  
    -   Il spécifie un modèle pour chaque type d'élément qui figure dans l'affichage de calendrier.  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  Remplacez la méthode `Button1_Click` de la classe `VisualWebPart1` par le code suivant.  Ce code ajoute des éléments issus de chaque calendrier sélectionné à l'affichage de calendrier principal.  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## Test du composant WebPart  
 Lorsque vous exécutez le projet, le site SharePoint s'ouvre.  Le composant WebPart est automatiquement ajouté à la galerie de composants WebPart dans SharePoint.  Pour tester ce projet, vous allez effectuer les tâches suivantes :  
  
-   ajouter un événement à chacune des deux listes de calendriers ;  
  
-   Ajoutez le composant WebPart à une page WebPart.  
  
-   Spécifiez les listes à inclure dans l'affichage de calendrier mensuel.  
  
#### Pour ajouter des événements aux listes de calendriers sur le site  
  
1.  Dans Visual Studio, appuyez sur la touche F5.  
  
     Le site SharePoint s'ouvre et la barre de lancement rapide de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] s'affiche dans la page.  
  
2.  Dans la barre de lancement rapide, sous **Listes**, choisissez le lien **Calendrier**.  
  
     La page **Calendrier** s'affiche.  
  
     Si aucun lien de calendrier n'apparaît sur la barre de lancement rapide, choisissez le lien **Contenu du site**.  Si la page Contenu de site n'affiche pas un élément **Calendrier**, créez\-en un.  
  
3.  Dans la page de calendrier, choisissez un jour, puis choisissez le lien **Ajouter** pour le jour sélectionné afin d'ajouter un événement.  
  
4.  Dans la zone **Titre**, entrez Événement dans le calendrier par défaut, puis choisissez le bouton **Enregistrer**.  
  
5.  Cliquez sur le lien **Contenu du site**, puis sélectionnez la vignette **Ajouter une application**.  
  
6.  Dans la page **Créer**, choisissez le type **Calendrier**, nommez le calendrier, puis choisissez le bouton **Créer**.  
  
7.  Ajoutez un événement au nouveau calendrier, nommez l'événement Événement dans le calendrier personnalisé, puis cliquez sur le bouton **Enregistrer**.  
  
#### Pour ajouter le composant WebPart à une page WebPart  
  
1.  Dans la page **Contenu du site**, ouvrez le dossier **Pages du site**.  
  
2.  Dans le ruban, choisissez l'onglet **Fichiers**, ouvrez le menu **Nouveau document**, puis choisissez la commande **Page de composants WebPart**.  
  
3.  Dans la page **Nouvelle page de composants WebPart**, nommez la page **SampleWebPartPage.aspx**, puis choisissez le bouton **Créer**.  
  
     La page de composants WebPart s'affiche.  
  
4.  Dans la zone supérieure de la page WebPart, choisissez l'onglet **Insérer**, puis cliquez sur le bouton **Composant WebPart**.  
  
5.  Sélectionnez le dossier **Personnalisé**, choisissez le composant WebPart **VisualWebPart1**, puis cliquez sur le bouton **Ajouter**.  
  
     Le composant WebPart s'affiche dans la page.  Les contrôles suivants s'affichent sur le composant WebPart :  
  
    -   Affichage de calendrier mensuel  
  
    -   Bouton **Mettre à jour**  
  
    -   Case à cocher **Calendrier**  
  
    -   Case à cocher **Calendrier personnalisé**  
  
#### Pour spécifier les listes à inclure dans l'affichage de calendrier mensuel  
  
1.  Dans le composant WebPart, spécifiez les calendriers que vous souhaitez inclure dans l'affichage de calendrier mensuel, puis choisissez le bouton **Mettre à jour**.  
  
     Les événements de tous les calendriers que vous avez spécifiés figurent dans l'affichage de calendrier mensuel.  
  
## Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procédure pas à pas : création d'un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  