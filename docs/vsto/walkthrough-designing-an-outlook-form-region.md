---
title: 'Procédure pas à pas : conception d’une zone de formulaire Outlook'
description: Découvrez comment vous pouvez concevoir une zone de formulaire Microsoft Outlook personnalisée qui s’affiche sous la forme d’une nouvelle page dans la fenêtre Inspecteur d’un élément de contact.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9eaa78a04c7dfda42a82a5d5a9ff3b407e6502d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842009"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Procédure pas à pas : conception d’une zone de formulaire Outlook
  Les zones de formulaire personnalisées étendent les formulaires Microsoft Office Outlook standard et personnalisés. Dans cette procédure pas à pas, vous allez concevoir une zone de formulaire personnalisée qui s'affiche comme une nouvelle page dans la fenêtre Inspecteur d'un élément de contact. Cette zone de formulaire affiche une carte de toutes les adresses répertoriées pour le contact, en envoyant les informations d’adresse au site web Windows Live Local Search. Pour plus d’informations sur les zones de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un projet de complément VSTO Outlook.

- Ajout d’une zone de formulaire au projet de complément VSTO

- Conception de la disposition de la zone de formulaire

- Personnalisation du comportement de la zone de formulaire

- Test de la zone de formulaire Outlook

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] ou plus récent.

  ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") Pour obtenir une version vidéo de cette rubrique, consultez [vidéo : concevoir une zone de formulaire Outlook](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Créer un projet de complément VSTO Outlook
 Commencez par créer un projet de complément VSTO de base.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Pour créer un projet de complément VSTO Outlook

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , créez un projet de complément VSTO Outlook portant le nom **MapItAddIn**.

2. Dans la boîte de dialogue **Nouveau projet** , sélectionnez **Créer le répertoire pour la solution**.

3. Enregistrez le projet dans un répertoire quelconque.

     Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Ajouter une zone de formulaire au projet de complément VSTO Outlook
 Une solution de complément VSTO Outlook peut contenir un ou plusieurs éléments de zone de formulaire Outlook. Ajoutez un élément de zone de formulaire à votre projet à l’aide de l’Assistant **nouvelle zone de formulaire Outlook** .

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Pour ajouter une zone de formulaire au projet de complément VSTO Outlook

1. Dans **Explorateur de solutions**, sélectionnez le projet **MapItAddIn** .

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **zone de formulaire Outlook**, nommez le fichier **MapIt**, puis cliquez sur **Ajouter**.

     L’Assistant **zone de formulaire NewOutlook** démarre.

4. Dans la page **Sélectionnez la méthode de création de la zone de formulaire** , cliquez sur **créer une nouvelle zone de formulaire**, puis cliquez sur **suivant**.

5. Dans la page **sélectionnez le type de zone de formulaire que vous souhaitez créer** , cliquez sur **séparer**, puis sur **suivant**.

     Une zone de formulaire *distincte* ajoute une nouvelle page à un formulaire Outlook. Pour plus d’informations sur les types de zones de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

6. Dans la page **fournir un texte descriptif et sélectionnez vos préférences d’affichage** , tapez **Map IT** dans la zone **nom** .

     Ce nom apparaît sur le ruban de la fenêtre Inspecteur lorsque l'élément de contact est ouvert.

7. Sélectionnez les **inspecteurs qui sont en mode composition** et les **inspecteurs qui sont en mode lecture**, puis cliquez sur **suivant**.

8. Dans la page **Identifiez les classes de message qui afficheront cette zone de formulaire** , effacez le **message électronique**, sélectionnez **contact**, puis cliquez sur **Terminer**.

     Un fichier *MapIt.cs* ou *MapIt. vb* est ajouté à votre projet.

## <a name="design-the-layout-of-the-form-region"></a>Concevoir la disposition de la zone de formulaire
 Développez visuellement des zones de formulaire à l’aide du *Concepteur de zones de formulaire*. Vous pouvez faire glisser des contrôles managés vers l'aire du Concepteur de zones de formulaire. Utilisez le concepteur et la fenêtre **Propriétés** pour ajuster la disposition et l’apparence des contrôles.

### <a name="to-design-the-layout-of-the-form-region"></a>Pour concevoir la disposition de la zone de formulaire

1. Dans **Explorateur de solutions**, développez le projet **MapItAddIn** , puis double-cliquez sur *MapIt.cs* ou *MapIt. vb* pour ouvrir le concepteur de zones de formulaire.

2. Cliquez avec le bouton droit sur le concepteur, puis cliquez sur **Propriétés**.

3. Dans la fenêtre **Propriétés** , affectez à **taille** la valeur **664, 469**.

     Cela garantit que la zone de formulaire sera suffisamment grande pour afficher une carte.

4. Dans le menu **Affichage** , cliquez sur **Boîte à outils**.

5. Dans l’onglet **contrôles communs** de la **boîte à outils**, ajoutez un **WebBrowser** à la zone de formulaire.

     Le **WebBrowser** affiche une carte de chaque adresse qui est indiquée pour le contact.

## <a name="customize-the-behavior-of-the-form-region"></a>Personnaliser le comportement de la zone de formulaire
 Ajoutez du code aux gestionnaires d'événements de zone de formulaire pour personnaliser la façon dont une zone de formulaire se comporte au moment de l'exécution. Pour cette zone de formulaire, le code examine les propriétés d'un élément Outlook et détermine s'il faut afficher la zone de formulaire Carte. S'il affiche la zone de formulaire, le code accède à Windows Live Local Search et charge une carte de toutes les adresses répertoriées dans l'élément de contact Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Pour personnaliser le comportement de la zone de formulaire

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *MapIt.cs* ou *MapIt. vb*, puis cliquez sur **afficher le code**.

    *MapIt.cs* ou *MapIt. vb* s’ouvre dans l’éditeur de code.

2. Développez la région de code de la **fabrique de zones de formulaire** .

    La classe de fabrique de zones de formulaire `MapItFactory` est exposée.

3. Ajoutez le code ci-après au gestionnaire d'événements `MapItFactory_FormRegionInitializing`. Ce gestionnaire d'événements est appelé quand l'utilisateur ouvre un élément de contact. Le code suivant détermine si l'élément de contact contient une adresse. Si l’élément de contact ne contient pas d’adresse, ce code affecte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> à la propriété de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe la **valeur true** et la zone de formulaire n’est pas affichée. Sinon, le complément VSTO déclenche l’événement <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> et affiche la zone de formulaire.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Ajoutez le code ci-après au gestionnaire d'événements <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Ce code effectue les tâches suivantes :

   - Concatène chaque adresse figurant dans l'élément de contact et crée une chaîne d'URL.

   - Appelle la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> de l'objet <xref:System.Windows.Forms.WebBrowser> et passe la chaîne d'URL en tant que paramètre.

     Le site web Local Search apparaît dans la zone de formulaire Carte et présente chaque adresse dans la zone temporaire.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Tester la zone de formulaire Outlook
 Quand vous exécutez le projet, Visual Studio ouvre Outlook. Ouvrez un élément de contact pour afficher la zone de formulaire Carte. La zone de formulaire Carte s'affiche en tant que page dans le formulaire de tout élément de contact contenant une adresse.

### <a name="to-test-the-map-it-form-region"></a>Pour tester la zone de formulaire Carte

1. Appuyez sur **F5** pour exécuter le projet.

     Outlook s'ouvre.

2. Dans Outlook, sous l’onglet dossier de **démarrage** , cliquez sur **nouveaux éléments**, puis sur **contact**.

3. Dans le formulaire de contact, tapez **Ann Royant** comme nom de contact, puis spécifiez les trois adresses suivantes.

    |Type d'adresse|Adresse|
    |------------------|-------------|
    |**Métier**|**4567 principale St. Buffalo, NY**|
    |**Page d'accueil**|**1234 nord du Saint-buffle, NY**|
    |**Autre**|**3456 principale St. Seattle, WA**|

4. Enregistrez et fermez l'élément de contact.

5. Rouvrez l’élément de contact **Anne Royant** .

    Dans Outlook, vous pouvez effectuer cette opération dans le groupe **Rechercher** en ouvrant le carnet d’adresses pour les contacts ou en tapant Ann Royant dans **Rechercher des personnes**.

6. Dans le groupe **Afficher** du ruban de l’élément, cliquez sur **mapper** pour ouvrir la zone de formulaire carte.

     La zone de formulaire Carte apparaît et affiche le site web Local Search. Les adresses **professionnelles**, **familiales** et **autres** s’affichent dans le panneau de travail. Dans la zone temporaire, sélectionnez une adresse que vous souhaitez cartographier.

## <a name="next-steps"></a>Étapes suivantes
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'une application Outlook, consultez les rubriques suivantes :

- Pour en savoir plus sur la personnalisation du ruban d’un élément Outlook, consultez [personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Voir aussi
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Instructions pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
