---
title: Créer un composant WebPart pour SharePoint à l’aide du concepteur
description: Dans cette procédure pas à pas, créez visuellement un composant WebPart à l’aide du modèle de projet composant Visual Web Part SharePoint dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 55f69875b06428c9bbe179e73dd6ea9b4ef40b8e
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112448"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Procédure pas à pas : créer un composant WebPart pour SharePoint à l’aide d’un concepteur

Si vous créez des composants WebPart pour un site SharePoint, vos utilisateurs peuvent directement modifier le contenu, l’apparence et le comportement des pages de ce site à l’aide d’un navigateur. Cette procédure pas à pas vous montre comment créer visuellement un composant WebPart à l’aide du modèle de projet **composant Visual Web part** SharePoint dans Visual Studio.

Le composant WebPart que vous allez créer affiche un affichage de calendrier mensuel et une case à cocher pour chaque liste de calendriers sur le site. Les utilisateurs peuvent spécifier les listes de calendriers à inclure dans l’affichage de calendrier mensuel en activant les cases à cocher.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un composant WebPart à l’aide du modèle de projet **composant Visual Web part** .
- Conception du composant WebPart à l’aide du concepteur Visual Web Developer dans Visual Studio.
- Ajout de code pour gérer les événements de contrôles sur le composant WebPart.
- Test du composant WebPart dans SharePoint.

    > [!NOTE]
    > Il se peut que votre ordinateur affiche des noms ou des emplacements différents pour certains éléments de l’interface utilisateur de Visual Studio dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Windows et SharePoint.

## <a name="create-a-web-part-project"></a>Créer un projet de composant WebPart

Tout d’abord, créez un projet de composant WebPart à l’aide du modèle de projet **composant Visual Web part** .

1. Commencez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] par utiliser l’option **exécuter en tant qu’administrateur** .

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.
::: moniker range="=vs-2017"

3. Dans la boîte de dialogue **nouveau projet** , sous **Visual C#** ou **Visual Basic**, développez **Office/SharePoint**, puis choisissez la catégorie **solutions SharePoint** .

4. Dans la liste des modèles, choisissez le modèle **SharePoint 2013-composant Visual Web part** , puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche. À l’aide de cet Assistant, vous pouvez spécifier le site que vous utiliserez pour déboguer le projet et le niveau de confiance de la solution.
::: moniker-end
::: moniker range=">=vs-2019"
3. Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le *projet vide SharePoint** pour la version particulière de SharePoint que vous avez installée. Par exemple, si vous avez SharePoint 2019 installer, sélectionnez le modèle **de projet sharepoint 2019-vide** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. Dans la zone **nom** , entrez **TestProject1**, puis cliquez sur le bouton **créer** .

::: moniker-end
5. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez la case **d’option déployer en tant que solution de batterie** .

6. Choisissez le bouton **Terminer** pour accepter le site SharePoint local par défaut.

## <a name="designing-the-web-part"></a>Conception du composant WebPart

Concevez le composant WebPart en ajoutant des contrôles de la **boîte à outils** à la surface du concepteur Visual Web Developer.

1. Dans le concepteur Visual Web Developer, choisissez l’onglet **conception** pour basculer vers mode création.

2. Dans la barre de menus, choisissez **Afficher** la  >  **boîte à outils**.

3. Dans le nœud **standard** de la **boîte à outils**, choisissez le contrôle **CheckBoxList** , puis effectuez l’une des étapes suivantes :

    - Ouvrez le menu contextuel du contrôle **CheckBoxList** , choisissez **copier**, ouvrez le menu contextuel de la première ligne dans le concepteur, puis choisissez **coller**.

    - Faites glisser le contrôle **CheckBoxList** de la **boîte à outils** et connectez le contrôle à la première ligne dans le concepteur.

4. Répétez l’étape précédente, mais déplacez un bouton sur la ligne suivante du concepteur.

5. Dans le concepteur, choisissez le bouton **Button1** .

6. Dans la barre de menus, choisissez **Afficher** la  >  **fenêtre Propriétés**.

     La fenêtre **Propriétés** apparaît.

7. Dans la propriété **Text** du bouton, entrez **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Gestion des événements de contrôles sur le composant WebPart

Ajoutez du code qui permet à l’utilisateur d’ajouter des calendriers à la vue de calendrier principal.

1. Effectuez l'un des ensembles d'étapes suivants :

   - Dans le concepteur, double-cliquez sur le bouton **mettre à jour** .

   - Dans la fenêtre **Propriétés** du bouton **mettre à jour** , choisissez le bouton **événements** . Dans la propriété **Click** , entrez **Button1_Click**, puis appuyez sur la touche entrée.

     Le fichier de code du contrôle utilisateur s’ouvre dans l’éditeur de code et le `Button1_Click` Gestionnaire d’événements s’affiche. Plus tard, vous ajouterez du code à ce gestionnaire d’événements.

2. Ajoutez les instructions suivantes au début du fichier de code du contrôle utilisateur.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. Ajoutez la ligne de code suivante à la `VisualWebPart1` classe. Ce code déclare un contrôle d’affichage de calendrier mensuel.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. Remplacez la `Page_Load` méthode de la `VisualWebPart1` classe par le code suivant. Ce code effectue les tâches suivantes :

   - Ajoute une vue de calendrier mensuelle au contrôle utilisateur.

   - Ajoute une case à cocher pour chaque liste de calendriers sur le site.

   - Spécifie un modèle pour chaque type d’élément qui s’affiche dans l’affichage de calendrier.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. Remplacez la `Button1_Click` méthode de la `VisualWebPart1` classe par le code suivant. Ce code ajoute des éléments de chaque calendrier sélectionné à l’affichage du calendrier principal.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>Tester le composant WebPart

Lorsque vous exécutez le projet, le site SharePoint s’ouvre. Le composant WebPart est automatiquement ajouté à la Galerie de composants WebPart dans SharePoint. Pour tester ce projet, vous allez effectuer les tâches suivantes :

- Ajoutez un événement à chacune des deux listes de calendriers distinctes.
- Ajoutez le composant WebPart à une page de composant WebPart.
- Spécifiez les listes à inclure dans l’affichage de calendrier mensuel.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Pour ajouter des événements aux listes de calendriers sur le site

1. Dans Visual Studio, appuyez sur la touche **F5** .

     Le site SharePoint s’ouvre et la [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barre lancement rapide apparaît sur la page.

2. Dans la barre lancement rapide, sous **listes**, choisissez le lien **calendrier** .

     La page **calendrier** s’affiche.

     Si vous ne voyez aucun lien de calendrier dans la barre lancement rapide, choisissez le lien **contenu du site** . Si la page contenu du site n’affiche pas d’élément de **calendrier** , créez-en une.

3. Sur la page calendrier, choisissez un jour, puis cliquez sur le lien **Ajouter** du jour sélectionné pour ajouter un événement.

4. Dans la zone **titre** , entrez **Event dans le calendrier par défaut**, puis choisissez le bouton **Enregistrer** .

5. Choisissez le lien **contenu du site** , puis choisissez la vignette **Ajouter une application** .

6. Dans la page **créer** , choisissez le type de **calendrier** , nommez le calendrier, puis choisissez le bouton **créer** .

7. Ajoutez un événement au nouveau calendrier, nommez l' **événement d’événement dans le calendrier personnalisé**, puis choisissez le bouton **Enregistrer** .

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Pour ajouter le composant WebPart à une page de composant WebPart

1. Dans la page **contenu du site** , ouvrez le dossier pages de **site** .

2. Dans le ruban, choisissez l’onglet **fichiers** , ouvrez le menu **nouveau document** , puis choisissez la commande **page de composants WebPart** .

3. Dans la page **nouvelle page de composant WebPart** , nommez la page **SampleWebPartPage. aspx**, puis choisissez le bouton **créer** .

     La page du composant WebPart s’affiche.

4. Dans la zone supérieure de la page de composant WebPart, cliquez sur l’onglet **Insérer** , puis choisissez le bouton **composant WebPart** .

5. Choisissez le dossier **personnalisé** , choisissez le composant WebPart **VisualWebPart1** , puis cliquez sur le bouton **Ajouter** .

     Le composant WebPart s’affiche sur la page. Les contrôles suivants apparaissent sur le composant WebPart :

    - Affichage de calendrier mensuel.

    - Bouton **mettre à jour** .

    - Une case à cocher **calendrier** .

    - Case à cocher **calendrier personnalisé** .

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Pour spécifier les listes à inclure dans l’affichage de calendrier mensuel

Dans le composant WebPart, spécifiez les calendriers que vous souhaitez inclure dans l’affichage de calendrier mensuel, puis choisissez le bouton **mettre à jour** .

Les événements de tous les calendriers que vous avez spécifiés s’affichent dans l’affichage du calendrier mensuel.

## <a name="see-also"></a>Voir aussi

[Créer des composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Procédure pas à pas : créer un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
