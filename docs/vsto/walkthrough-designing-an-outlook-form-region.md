---
title: 'Procédure pas à pas : Concevoir une zone de formulaire Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 693261bb6894681b613ad0db2f0b3c116109a782
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813685"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Procédure pas à pas : Concevoir une zone de formulaire Outlook
  Les zones de formulaire personnalisées étendent les formulaires Microsoft Office Outlook standard et personnalisés. Dans cette procédure pas à pas, vous allez concevoir une zone de formulaire personnalisée qui s'affiche comme une nouvelle page dans la fenêtre Inspecteur d'un élément de contact. Cette zone de formulaire affiche une carte de toutes les adresses répertoriées pour le contact, en envoyant les informations d’adresse au site web Windows Live Local Search. Pour plus d’informations sur les zones de formulaire, consultez [zones de formulaire Outlook créer](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de complément VSTO Outlook  
  
-   Ajout d'une zone de formulaire au projet de complément VSTO  
  
-   Conception de la disposition de la zone de formulaire  
  
-   Personnalisation du comportement de la zone de formulaire  
  
-   Test de la zone de formulaire Outlook  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] ou [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
  ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour obtenir une version vidéo de cette rubrique, consultez [vidéo Comment : concevoir une zone de formulaire Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="create-a-new-outlook-vsto-add-in-project"></a>Créer un nouveau projet de complément Outlook VSTO  
 Commencez par créer un projet de complément VSTO de base.  
  
### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Pour créer un projet de complément VSTO Outlook  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créer un projet de complément Outlook VSTO portant le nom **MapItAddIn**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** , sélectionnez **Créer le répertoire pour la solution**.  
  
3.  Enregistrez le projet dans un répertoire quelconque.  
  
     Pour plus d’informations, consultez [Comment : les projets Office de créer dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Ajouter une zone de formulaire au projet de complément Outlook VSTO  
 Une solution de complément VSTO Outlook peut contenir un ou plusieurs éléments de zone de formulaire Outlook. Ajouter un élément de zone de formulaire à votre projet à l’aide de la **nouvelle zone de formulaire Outlook** Assistant.  
  
### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Pour ajouter une zone de formulaire au projet de complément VSTO Outlook  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le **MapItAddIn** projet.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **zone de formulaire Outlook**, nommez le fichier **MapIt**, puis cliquez sur **ajouter**.  
  
     Le **zone de formulaire NewOutlook** Assistant démarre.  
  
4.  Sur le **Choisissez comment vous souhaitez créer la zone de formulaire** , cliquez sur **concevoir une zone de formulaire**, puis cliquez sur **suivant**.  
  
5.  Sur le **sélectionner le type de zone de formulaire que vous souhaitez créer** , cliquez sur **distinct**, puis cliquez sur **suivant**.  
  
     Un *distinct* zone de formulaire ajoute une nouvelle page à un formulaire Outlook. Pour plus d’informations sur les types de zones de formulaire, consultez [zones de formulaire Outlook créer](../vsto/creating-outlook-form-regions.md).  
  
6.  Sur le **fournissez un texte descriptif et sélectionnez vos préférences d’affichage** , tapez **carte** dans le **nom** boîte.  
  
     Ce nom apparaît sur le ruban de la fenêtre Inspecteur lorsque l'élément de contact est ouvert.  
  
7.  Sélectionnez **inspecteurs qui sont en mode de composition** et **inspecteurs qui sont en mode lecture**, puis cliquez sur **suivant**.  
  
8.  Sur le **Identifiez les classes de message qui afficheront cette zone de formulaire** page, désactivez **Message électronique**, sélectionnez **Contact**, puis cliquez sur **Terminer**.  
  
     Un *MapIt.cs* ou *MapIt.vb* fichier est ajouté à votre projet.  
  
## <a name="design-the-layout-of-the-form-region"></a>Concevoir la disposition de la zone de formulaire  
 Pour développer visuellement des zones de formulaire à l’aide de la *Concepteur de zones de formulaire*. Vous pouvez faire glisser des contrôles managés vers l'aire du Concepteur de zones de formulaire. Utilisez le concepteur et le **propriétés** fenêtre pour ajuster la disposition du contrôle et l’apparence.  
  
### <a name="to-design-the-layout-of-the-form-region"></a>Pour concevoir la disposition de la zone de formulaire  
  
1.  Dans **l’Explorateur de solutions**, développez le **MapItAddIn** de projet, puis double-cliquez sur *MapIt.cs* ou *MapIt.vb* pour ouvrir la zone de formulaire Concepteur.  
  
2.  Cliquez sur le concepteur, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés** fenêtre, définissez **taille** à **664, 469**.  
  
     Cela garantit que la zone de formulaire sera suffisamment grande pour afficher une carte.  
  
4.  Dans le menu **Affichage** , cliquez sur **Boîte à outils**.  
  
5.  À partir de la **contrôles communs** onglet de la **boîte à outils**, ajoutez un **WebBrowser** vers la zone de formulaire.  
  
     Le **WebBrowser** affiche une carte de toutes les adresses répertoriées pour le contact.  
  
## <a name="customize-the-behavior-of-the-form-region"></a>Personnaliser le comportement de la zone de formulaire  
 Ajoutez du code aux gestionnaires d'événements de zone de formulaire pour personnaliser la façon dont une zone de formulaire se comporte au moment de l'exécution. Pour cette zone de formulaire, le code examine les propriétés d'un élément Outlook et détermine s'il faut afficher la zone de formulaire Carte. S'il affiche la zone de formulaire, le code accède à Windows Live Local Search et charge une carte de toutes les adresses répertoriées dans l'élément de contact Outlook.  
  
### <a name="to-customize-the-behavior-of-the-form-region"></a>Pour personnaliser le comportement de la zone de formulaire  
  
1. Dans **l’Explorateur de solutions**, avec le bouton droit cliquez sur *MapIt.cs* ou *MapIt.vb*, puis cliquez sur **afficher le Code**.  
  
    *MapIt.cs* ou *MapIt.vb* s’ouvre dans l’éditeur de Code.  
  
2. Développez le **fabrique de zones de formulaire** région de code.  
  
    La classe de fabrique de zones de formulaire `MapItFactory` est exposée.  
  
3. Ajoutez le code ci-après au gestionnaire d'événements `MapItFactory_FormRegionInitializing`. Ce gestionnaire d'événements est appelé quand l'utilisateur ouvre un élément de contact. Le code suivant détermine si l'élément de contact contient une adresse. Si l’élément de contact ne contient pas une adresse, ce code définit le <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété de la <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe **true** et la zone de formulaire n’est pas affichée. Sinon, le complément VSTO déclenche l’événement <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> et affiche la zone de formulaire.  
  
    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4. Ajoutez le code ci-après au gestionnaire d'événements <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Ce code exécute les tâches suivantes :  
  
   - Concatène chaque adresse figurant dans l'élément de contact et crée une chaîne d'URL.  
  
   - Appelle la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> de l'objet <xref:System.Windows.Forms.WebBrowser> et passe la chaîne d'URL en tant que paramètre.  
  
     Le site web Local Search apparaît dans la zone de formulaire Carte et présente chaque adresse dans la zone temporaire.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="test-the-outlook-form-region"></a>Tester la zone de formulaire Outlook  
 Quand vous exécutez le projet, Visual Studio ouvre Outlook. Ouvrez un élément de contact pour afficher la zone de formulaire Carte. La zone de formulaire Carte s'affiche en tant que page dans le formulaire de tout élément de contact contenant une adresse.  
  
### <a name="to-test-the-map-it-form-region"></a>Pour tester la zone de formulaire Carte  
  
1.  Appuyez sur **F5** pour exécuter le projet.  
  
     Outlook s'ouvre.  
  
2.  Dans Outlook, sur le **accueil** , cliquez sur **nouveaux éléments**, puis cliquez sur **Contact**.  
  
3.  Dans le formulaire de contact, tapez **Ann Beebe** comme contact de nommer et spécifiez les trois adresses suivantes.  
  
    |Type d'adresse|Adresse|  
    |------------------|-------------|  
    |**Entreprise**|**4567 Main St. Buffalo, New York**|  
    |**Accueil**|**1234 Nord St. Buffalo, New York**|  
    |**Autre**|**3456 Main St. Seattle, WA**|  
  
4.  Enregistrez et fermez l'élément de contact.  
  
5.  Rouvrez le **Ann Beebe** élément de contact.  
  
6.  Dans le **afficher** groupe du ruban de l’élément, cliquez sur **carte** pour ouvrir la zone de formulaire carte.  
  
     La zone de formulaire Carte apparaît et affiche le site web Local Search. Le **Business**, **accueil**, et **autres** adresses s’affichent dans la zone temporaire. Dans la zone temporaire, sélectionnez une adresse que vous souhaitez cartographier.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'une application Outlook, consultez les rubriques suivantes :  
  
-   Pour savoir comment personnaliser le ruban d’un élément Outlook, consultez [personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder à une zone de formulaire lors de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Instructions pour créer des zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procédure pas à pas : Importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Comment : empêcher Outlook d’afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  