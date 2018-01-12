---
title: "Procédure pas à pas : Création d’un composant WebPart pour SharePoint à l’aide d’un concepteur | Documents Microsoft"
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 28be854f01234783ff9873753eb88ca92bc192d6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>Procédure pas à pas : création d'un composant WebPart pour SharePoint à l'aide d'un concepteur
  Si vous créez des composants WebPart pour un site SharePoint, les utilisateurs peuvent modifier directement le contenu, l’apparence et comportement des pages de ce site à l’aide d’un navigateur. Cette procédure pas à pas vous montre comment créer un composant WebPart visuellement à l’aide de SharePoint **composant Visual Web Part** modèle de projet dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Le composant WebPart que vous allez créer affiche un affichage de calendrier mensuel et une case à cocher pour chaque liste de calendriers sur le site. Les utilisateurs peuvent spécifier les listes de calendriers à inclure dans l’affichage de calendrier mensuel en activant les cases à cocher.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un composant WebPart à l’aide de la **composant Visual Web Part** modèle de projet.  
  
-   Conception du composant WebPart à l’aide du concepteur Visual Web Developer dans Visual Studio.  
  
-   Ajout de code pour gérer les événements de contrôles sur le composant WebPart.  
  
-   Tester le composant WebPart dans SharePoint.  
  
    > [!NOTE]  
    >  Votre ordinateur peut afficher des noms différents ou des emplacements pour certains éléments de l’interface utilisateur pour Visual Studio dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint. Consultez [configuration requise pour développer des Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]ou version supérieure.  
  
## <a name="creating-a-web-part-project"></a>Création d’un projet de composant WebPart  
 Commencez par créer un projet de composant WebPart à l’aide de la **composant Visual Web Part** modèle de projet.  
  
#### <a name="to-create-a-visual-web-part-project"></a>Pour créer un projet de composant Visual Web Part  
  
1.  Démarrer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à l’aide de la **exécuter en tant qu’administrateur** option.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
3.  Dans le **nouveau projet** boîte de dialogue, sous **Visual C#** ou **Visual Basic**, développez **Office/SharePoint**, puis choisissez le  **Les Solutions SharePoint** catégorie.  
  
4.  Dans la liste des modèles, choisissez le **SharePoint 2013 - composant Visual Web Part** modèle, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche. À l’aide de cet Assistant, vous pouvez spécifier le site que vous allez utiliser pour déboguer le projet et le niveau de confiance de la solution.  
  
5.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer une solution de batterie de serveurs** case d’option.  
  
6.  Choisissez le **Terminer** bouton pour accepter le site SharePoint local par défaut.  
  
## <a name="designing-the-web-part"></a>Conception du composant WebPart  
 Concevoir le composant WebPart en ajoutant des contrôles à partir de la **boîte à outils** vers l’aire du concepteur Visual Web Developer.  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>Pour concevoir la disposition du composant WebPart  
  
1.  Dans le concepteur Visual Web Developer, cliquez sur le **conception** tab pour passer en mode Design.  
  
2.  Dans la barre de menus, choisissez **Affichage**, **Boîte à outils**.  
  
3.  Dans le **Standard** nœud de la **boîte à outils**, choisissez le **liste case à cocher** contrôler, puis effectuez l’une des étapes suivantes :  
  
    -   Ouvrez le menu contextuel pour le **liste case à cocher** contrôler, choisissez **copie**, ouvrez le menu contextuel de la première ligne dans le concepteur, puis choisissez **coller**.  
  
    -   Faites glisser le **liste case à cocher** contrôle depuis la **boîte à outils**et connecter le contrôle à la première ligne dans le concepteur.  
  
4.  Répétez l’étape précédente, mais les déplacer d’un bouton à la ligne suivante du concepteur.  
  
5.  Dans le concepteur, choisissez le **Button1** bouton.  
  
6.  Dans la barre de menus, choisissez **vue**, **fenêtre Propriétés**.  
  
     Le **propriétés** fenêtre s’ouvre.  
  
7.  Dans le **texte** propriété du bouton, entrez **mise à jour**.  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestion des événements des contrôles sur le composant WebPart  
 Ajoutez le code qui permet à l’utilisateur Ajouter des calendriers à l’affichage de calendrier principal.  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>Pour gérer les événements de contrôles sur le composant WebPart  
  
1.  Effectuez l'un des ensembles d'étapes suivants :  
  
    -   Dans le concepteur, double-cliquez sur le **mise à jour** bouton.  
  
    -   Dans le **propriétés** fenêtre pour le **mise à jour** bouton, choisissez la **événements** bouton. Dans le **cliquez sur** propriété, entrez **Button1_Click**, puis appuyez sur ENTRÉE.  
  
     Le fichier de code du contrôle utilisateur s’ouvre dans l’éditeur de Code et le `Button1_Click` Gestionnaire d’événements s’affiche. Une version ultérieure, vous ajouterez du code à ce gestionnaire d’événements.  
  
2.  Ajoutez les instructions suivantes en haut du fichier de code du contrôle utilisateur.  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  Ajoutez la ligne suivante de code pour la `VisualWebPart1` classe. Ce code déclare un contrôle calendrier mensuel.  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  Remplacez le `Page_Load` méthode de la `VisualWebPart1` classe par le code suivant. Ce code exécute les tâches suivantes :  
  
    -   Ajoute un affichage de calendrier mensuel au contrôle utilisateur.  
  
    -   Ajoute une case à cocher pour chaque liste de calendriers sur le site.  
  
    -   Spécifie un modèle pour chaque type d’élément qui apparaît dans le calendrier.  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  Remplacez le `Button1_Click` méthode de la `VisualWebPart1` classe par le code suivant. Ce code ajoute des éléments de chaque calendrier sélectionné à l’affichage de calendrier principal.  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>Le composant WebPart de test  
 Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Le composant WebPart est automatiquement ajouté à la galerie de composants WebPart dans SharePoint. Pour tester ce projet, vous allez effectuer les tâches suivantes :  
  
-   Ajouter un événement à chacune des deux listes de calendriers.  
  
-   Ajouter le composant WebPart à une page WebPart.  
  
-   Spécifiez les listes à inclure dans l’affichage de calendrier mensuel.  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Pour ajouter des événements à des listes de calendrier sur le site  
  
1.  Dans Visual Studio, appuyez sur la touche F5.  
  
     Le site SharePoint s’ouvre et le [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barre de lancement rapide s’affiche sur la page.  
  
2.  Dans la barre de lancement rapide, sous **répertorie**, choisissez le **calendrier** lien.  
  
     Le **calendrier** page s’affiche.  
  
     Si aucun lien de calendrier s’affiche dans la barre de lancement rapide, choisissez le **le contenu du Site** lien. Si la page de contenu du Site n’affiche pas une **calendrier** d’élément, créez-en un.  
  
3.  Dans la page Calendrier, choisissez un jour, puis le **ajouter** lien dans le jour sélectionné pour ajouter un événement.  
  
4.  Dans le **titre** , entrez **événement dans le calendrier par défaut**, puis choisissez le **enregistrer** bouton.  
  
5.  Choisissez le **le contenu du Site** lier, puis choisissez le **ajouter une application** vignette.  
  
6.  Sur le **créer** page, choisissez la **calendrier** de type, nommez le calendrier, puis choisissez le **créer** bouton.  
  
7.  Ajouter un événement pour le nouveau calendrier, le nom de l’événement **événement dans le calendrier personnalisé**, puis choisissez le **enregistrer** bouton.  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>Pour ajouter le composant WebPart à une page de composants WebPart  
  
1.  Sur le **le contenu du Site** page, ouvrez le **Pages du Site** dossier.  
  
2.  Dans le ruban, cliquez sur le **fichiers** onglet, ouvrez le **Nouveau Document** menu, puis choisissez le **Page WebPart** commande.  
  
3.  Sur le **nouvelle Page WebPart** page, nommez la page **SampleWebPartPage.aspx**, puis choisissez le **créer** bouton.  
  
     La page de composants WebPart s’affiche.  
  
4.  Dans la zone supérieure de la page de composants WebPart, choisissez le **insérer** onglet, puis choisissez le **WebPart** bouton.  
  
5.  Choisissez le **personnalisé** dossier, choisissez le **VisualWebPart1** WebPart, puis choisissez le **ajouter** bouton.  
  
     Le composant WebPart apparaît sur la page. Les contrôles suivants s’affichent dans le composant WebPart :  
  
    -   Un affichage de calendrier mensuel.  
  
    -   Un **mise à jour** bouton.  
  
    -   A **calendrier** case à cocher.  
  
    -   A **calendrier personnalisé** case à cocher.  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Pour spécifier des listes à inclure dans l’affichage de calendrier mensuel  
  
1.  Dans le composant WebPart, spécifier des calendriers que vous souhaitez inclure dans l’affichage de calendrier mensuel, puis choisissez le **mise à jour** bouton.  
  
     Événements de tous les calendriers que vous avez spécifié s’affichent dans l’affichage de calendrier mensuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procédure pas à pas : création d’un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  