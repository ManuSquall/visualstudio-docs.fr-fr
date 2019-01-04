---
title: 'Procédure pas à pas : Création d’un composant WebPart pour SharePoint à l’aide d’un concepteur | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 146a1722f240895e0f508b0474df72f6f5f84ece
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870905"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Procédure pas à pas : Créer un composant WebPart pour SharePoint à l’aide d’un concepteur

Si vous créez des composants WebPart pour un site SharePoint, vos utilisateurs peuvent modifier directement le contenu, l’apparence et comportement des pages de ce site à l’aide d’un navigateur. Cette procédure pas à pas vous montre comment créer un composant WebPart visuellement à l’aide de SharePoint **composant Visual Web Part** modèle de projet dans Visual Studio.

Le composant WebPart que vous créerez affiche un affichage de calendrier mensuel et une case à cocher pour chaque liste de calendriers sur le site. Les utilisateurs peuvent spécifier les listes de calendriers à inclure dans l’affichage de calendrier mensuel en activant les cases à cocher.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un composant WebPart à l’aide de la **composant Visual Web Part** modèle de projet.
- Conception du composant WebPart à l’aide du concepteur Visual Web Developer dans Visual Studio.
- Ajout de code pour gérer les événements de contrôles sur le composant WebPart.
- Tester le composant WebPart dans SharePoint.

    > [!NOTE]
    > Votre ordinateur peut afficher des noms différents ou des emplacements pour certains éléments de l’interface utilisateur pour Visual Studio dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge de Windows et SharePoint.

## <a name="create-a-web-part-project"></a>Créer un projet de composant WebPart

Tout d’abord, créez un projet de composant WebPart à l’aide de la **composant Visual Web Part** modèle de projet.

1. Démarrer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à l’aide de la **exécuter en tant qu’administrateur** option.

2. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans la **nouveau projet** boîte de dialogue, sous une ou l’autre **Visual C#** ou **de Visual Basic**, développez **Office/SharePoint**, puis cliquez sur le  **Solutions SharePoint** catégorie.

4. Dans la liste des modèles, choisissez le **SharePoint 2013 - composant Visual Web Part** modèle, puis choisissez le **OK** bouton.

     Le **Assistant Personnalisation de SharePoint** s’affiche. À l’aide de cet Assistant, vous pouvez spécifier le site que vous allez utiliser pour déboguer le projet et le niveau de confiance de la solution.

5. Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer en tant que solution de batterie** case d’option.

6. Choisissez le **Terminer** bouton pour accepter le site SharePoint local par défaut.

## <a name="designing-the-web-part"></a>Conception du composant WebPart

Concevez le composant WebPart en ajoutant des contrôles à partir de la **boîte à outils** vers l’aire du concepteur Visual Web Developer.

1. Dans le concepteur Visual Web Developer, choisissez le **conception** tab pour passer en mode Design.

2. Dans la barre de menus, choisissez **Affichage** > **Boîte à outils**.

3. Dans le **Standard** nœud de la **boîte à outils**, choisissez le **CheckBoxList** contrôler, puis effectuez l’une des étapes suivantes :

    - Ouvrez le menu contextuel pour le **CheckBoxList** contrôler, choisissez **copie**, ouvrez le menu contextuel pour la première ligne dans le concepteur, puis choisissez **coller**.

    - Faites glisser le **CheckBoxList** contrôle depuis la **boîte à outils**et connecter le contrôle à la première ligne dans le concepteur.

4. Répétez l’étape précédente, mais le déplacement d’un bouton à la ligne suivante du concepteur.

5. Dans le concepteur, choisissez le **Button1** bouton.

6. Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.

     Le **propriétés** fenêtre s’ouvre.

7. Dans le **texte** propriété du bouton, entrez **mise à jour**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestion des événements de contrôles sur le composant WebPart

Ajoutez le code qui permet à l’utilisateur Ajouter des calendriers à l’affichage de calendrier principal.

1. Effectuez l'un des ensembles d'étapes suivants :

   - Dans le concepteur, double-cliquez sur le **mise à jour** bouton.

   - Dans le **propriétés** fenêtre pour le **mise à jour** bouton, choisissez la **événements** bouton. Dans le **cliquez sur** propriété, entrez **Button1_Click**, puis choisissez la touche ENTRÉE.

     Le fichier de code du contrôle utilisateur s’ouvre dans l’éditeur de Code et le `Button1_Click` Gestionnaire d’événements s’affiche. Une version ultérieure, vous ajouterez du code à ce gestionnaire d’événements.

2. Ajoutez les instructions suivantes au début du fichier de code du contrôle utilisateur.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Ajoutez la ligne suivante de code pour le `VisualWebPart1` classe. Ce code déclare un contrôle d’affichage de calendrier mensuel.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Remplacez le `Page_Load` méthode de la `VisualWebPart1` classe par le code suivant. Ce code exécute les tâches suivantes :

   - Ajoute un affichage de calendrier mensuel au contrôle utilisateur.

   - Ajoute une case à cocher pour chaque liste de calendriers sur le site.

   - Spécifie un modèle pour chaque type d’élément qui apparaît dans l’affichage de calendrier.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Remplacez le `Button1_Click` méthode de la `VisualWebPart1` classe par le code suivant. Ce code ajoute des éléments à partir de chaque calendrier sélectionné à l’affichage de calendrier principal.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Tester le composant WebPart

Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Le composant WebPart est automatiquement ajouté à la galerie de composants WebPart dans SharePoint. Pour tester ce projet, vous allez effectuer les tâches suivantes :

- Ajouter un événement à chacune des deux listes de calendriers.
- Ajouter le composant WebPart à une page WebPart.
- Spécifiez les listes à inclure dans l’affichage de calendrier mensuel.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Pour ajouter des événements aux listes de calendriers sur le site

1. Dans Visual Studio, choisissez le **F5** clé.

     Le site SharePoint s’ouvre et le [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barre de lancement rapide s’affiche sur la page.

2. Dans la barre de lancement rapide, sous **répertorie**, choisissez le **calendrier** lien.

     Le **calendrier** page s’affiche.

     Si aucun lien de calendrier s’affiche dans la barre de lancement rapide, choisissez le **contenu du Site** lien. Si la page de contenu du Site n’affiche pas un **calendrier** d’élément, créez-en un.

3. Dans la page Calendrier, choisissez un jour, puis le **ajouter** lien dans le jour sélectionné pour ajouter un événement.

4. Dans le **titre** , entrez **événement dans le calendrier par défaut**, puis choisissez le **enregistrer** bouton.

5. Choisissez le **contenu du Site** lier, puis choisissez le **ajouter une application** vignette.

6. Sur le **créer** page, choisissez le **calendrier** tapez, nommez le calendrier, puis choisissez le **créer** bouton.

7. Ajouter un événement pour le nouveau calendrier, nommez l’événement **événement dans le calendrier personnalisé**, puis choisissez le **enregistrer** bouton.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Pour ajouter le composant WebPart à une page WebPart

1. Sur le **contenu du Site** page, ouvrez le **Pages de Site** dossier.

2. Dans le ruban, choisissez le **fichiers** onglet, ouvrez le **Nouveau Document** menu, puis choisissez le **Page WebPart** commande.

3. Sur le **nouvelle Page de composants WebPart** page, nommez la page **SampleWebPartPage.aspx**, puis choisissez le **créer** bouton.

     La page de composants WebPart s’affiche.

4. Dans la zone supérieure de la page de composants WebPart, choisissez le **insérer** onglet, puis choisissez le **WebPart** bouton.

5. Choisissez le **personnalisé** dossier, choisissez le **VisualWebPart1** WebPart, puis choisissez le **ajouter** bouton.

     Le composant WebPart apparaît sur la page. Les contrôles suivants s’affichent dans le composant WebPart :

    - Un affichage de calendrier mensuel.

    - Un **mise à jour** bouton.

    - Un **calendrier** case à cocher.

    - Un **calendrier personnalisé** case à cocher.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Pour spécifier les listes à inclure dans l’affichage de calendrier mensuel

Dans le composant WebPart, spécifiez les calendriers que vous souhaitez inclure dans l’affichage de calendrier mensuel, puis choisissez le **mise à jour** bouton.

Événements à partir de tous les calendriers que vous avez spécifié s’affichent dans l’affichage de calendrier mensuel.

## <a name="see-also"></a>Voir aussi

[Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Guide pratique pour Créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Procédure pas à pas : Créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
