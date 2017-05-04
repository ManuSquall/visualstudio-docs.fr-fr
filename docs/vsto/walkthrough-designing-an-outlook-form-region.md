---
title: "Proc&#233;dure pas &#224; pas&#160;: conception d&#39;une zone de formulaire Outlook | Microsoft Docs"
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
helpviewer_keywords: 
  - "zones de formulaire (développement Office dans Visual Studio), créer"
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Proc&#233;dure pas &#224; pas&#160;: conception d&#39;une zone de formulaire Outlook
  Les zones de formulaire personnalisées étendent les formulaires Microsoft Office Outlook standard et personnalisés.  Dans cette procédure pas à pas, vous allez concevoir une zone de formulaire personnalisée qui s'affiche comme une nouvelle page dans la fenêtre Inspecteur d'un élément de contact.  Cette zone de formulaire affiche une carte de toutes les adresses répertoriées pour le contact, en envoyant les informations d'adresse au site web Windows Live Local Search.  Pour obtenir des informations sur les zones de formulaire, consultez [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d'un projet de complément VSTO Outlook  
  
-   Ajout d'une zone de formulaire au projet de complément VSTO  
  
-   Conception de la disposition de la zone de formulaire  
  
-   Personnalisation du comportement de la zone de formulaire  
  
-   Test de la zone de formulaire Outlook  
  
> [!NOTE]  
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.  L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] ou [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner la version vidéo de cette rubrique, consultez [Vidéo : conception d'une zone de formulaire Outlook](http://go.microsoft.com/fwlink/?LinkId=140824).  
  
## Création d'un projet de complément VSTO Outlook  
 Commencez par créer un projet de complément VSTO de base.  
  
#### Pour créer un projet de complément VSTO Outlook  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de complément VSTO Outlook et nommez\-le MapItAddIn.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Créer le répertoire pour la solution**.  
  
3.  Enregistrez le projet dans un répertoire quelconque.  
  
     Pour plus d'informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Ajout d'une zone de formulaire au projet de complément VSTO Outlook  
 Une solution de complément VSTO Outlook peut contenir un ou plusieurs éléments de zone de formulaire Outlook.  Ajoutez un élément de zone de formulaire à votre projet à l'aide de l'Assistant **Nouvelle zone de formulaire Outlook**.  
  
#### Pour ajouter une zone de formulaire au projet de complément VSTO Outlook  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez le projet **MapItAddIn**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Zone de formulaire Outlook**, nommez le fichier MapIt, puis cliquez sur **Ajouter**.  
  
     L'Assistant **Nouvellezone de formulaire Outlook** démarre.  
  
4.  Dans la page **Sélectionnez la méthode de création de la zone de formulaire**, cliquez sur **Créer une nouvelle zone de formulaire**, puis cliquez sur **Suivant**.  
  
5.  Dans la page **Sélectionnez le type de zone de formulaire que vous souhaitez créer**, cliquez sur **Séparer**, puis sur **Suivant**.  
  
     Une zone de formulaire *distincte* ajoute une nouvelle page à un formulaire Outlook.  Pour plus d'informations sur les types de zone de formulaire, consultez [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).  
  
6.  Dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d'affichage**, tapez **Carte** dans la zone **Nom**.  
  
     Ce nom apparaît sur le ruban de la fenêtre Inspecteur lorsque l'élément de contact est ouvert.  
  
7.  Sélectionnez **Inspecteurs qui sont en mode composition** et **Inspecteurs qui sont en mode lecture**, puis cliquez sur **Suivant**.  
  
8.  Dans la page **Identifiez les classes de message qui afficheront cette zone de formulaire**, désélectionnez **Message**, sélectionnez **Contact**, puis cliquez sur **Terminer**.  
  
     Un fichier MapIt.cs ou MapIt.vb est ajouté à votre projet.  
  
## Conception de la disposition de la zone de formulaire  
 Développez visuellement des zones de formulaire en utilisant le *Concepteur de zones de formulaire*.  Vous pouvez faire glisser des contrôles managés vers l'aire du Concepteur de zones de formulaire.  Utilisez le concepteur et la fenêtre **Propriétés** pour ajuster la disposition et l'apparence des contrôles.  
  
#### Pour concevoir la disposition de la zone de formulaire  
  
1.  Dans l'**Explorateur de solutions**, développez le projet **MapItAddIn**, puis double\-cliquez sur MapIt.cs ou MapIt.vb pour ouvrir le Concepteur de zones de formulaire.  
  
2.  Cliquez avec le bouton droit sur le concepteur et cliquez sur **Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, définissez **Taille** sur 664, 469.  
  
     Cela garantit que la zone de formulaire sera suffisamment grande pour afficher une carte.  
  
4.  Dans le menu **Affichage**, cliquez sur **Boîte à outils**.  
  
5.  Sous l'onglet **Contrôles communs** de la **Boîte à outils**, ajoutez un **WebBrowser** à la zone de formulaire.  
  
     Le **WebBrowser** affiche une carte de toutes les adresses répertoriées pour le contact.  
  
## Personnalisation du comportement de la zone de formulaire  
 Ajoutez du code aux gestionnaires d'événements de zone de formulaire pour personnaliser la façon dont une zone de formulaire se comporte au moment de l'exécution.  Pour cette zone de formulaire, le code examine les propriétés d'un élément Outlook et détermine s'il faut afficher la zone de formulaire Carte.  S'il affiche la zone de formulaire, le code accède à Windows Live Local Search et charge une carte de toutes les adresses répertoriées dans l'élément de contact Outlook.  
  
#### Pour personnaliser le comportement de la zone de formulaire  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur MapIt.cs ou sur MapIt.vb, puis cliquez sur **Afficher le code**.  
  
     MapIt.cs ou MapIt.vb s'ouvre dans l'éditeur de code.  
  
2.  Développez la zone de code **Fabrique de zones de formulaire**.  
  
     La classe de fabrique de zones de formulaire `MapItFactory` est exposée.  
  
3.  Ajoutez le code ci\-après au gestionnaire d'événements `MapItFactory_FormRegionInitializing`.  Ce gestionnaire d'événements est appelé quand l'utilisateur ouvre un élément de contact.  Le code suivant détermine si l'élément de contact contient une adresse.  Si l'élément de contact ne contient pas d'adresse, ce code affecte à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de la classe <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> la valeur **true** et la zone de formulaire n'est pas affichée.  Sinon, le complément VSTO déclenche l'événement <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> et affiche la zone de formulaire.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
4.  Ajoutez le code ci\-après au gestionnaire d'événements <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>.  Ce code exécute les tâches suivantes :  
  
    -   Concatène chaque adresse figurant dans l'élément de contact et crée une chaîne d'URL.  
  
    -   Appelle la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> de l'objet <xref:System.Windows.Forms.WebBrowser> et passe la chaîne d'URL en tant que paramètre.  
  
     Le site web Local Search apparaît dans la zone de formulaire Carte et présente chaque adresse dans la zone temporaire.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#2)]  
  
## Test de la zone de formulaire Outlook  
 Quand vous exécutez le projet, Visual Studio ouvre Outlook.  Ouvrez un élément de contact pour afficher la zone de formulaire Carte.  La zone de formulaire Carte s'affiche en tant que page dans le formulaire de tout élément de contact contenant une adresse.  
  
#### Pour tester la zone de formulaire Carte  
  
1.  Appuyez sur F5 pour exécuter le projet.  
  
     Outlook s'ouvre.  
  
2.  Dans Outlook, sous l'onglet **Accueil**, cliquez sur **Nouveaux éléments**, puis sur **Contact**.  
  
3.  Dans le formulaire du contact, tapez **Sabine Royant** comme nom de contact, puis spécifiez les trois adresses suivantes.  
  
    |Type d'adresse|Adresse|  
    |--------------------|-------------|  
    |**Bureau**|45, rue principale  69005 Lyon|  
    |**Accueil**|123, rue Duguesclin  69005 Lyon|  
    |**Autre**|345, rue de la République  75008 Paris|  
  
4.  Enregistrez et fermez l'élément de contact.  
  
5.  Rouvrez l'élément de contact **Sabine Royant**.  
  
6.  Dans le groupe **Afficher** du ruban de l'élément, cliquez sur **Carte** pour ouvrir la zone de formulaire Carte.  
  
     La zone de formulaire Carte apparaît et affiche le site web Local Search.  Les adresses **Bureau**, **Domicile** et **Autre** apparaissent dans la zone temporaire.  Dans la zone temporaire, sélectionnez une adresse que vous souhaitez cartographier.  
  
## Étapes suivantes  
 Pour plus d'informations sur la personnalisation de l'interface utilisateur d'une application Outlook, consultez les rubriques suivantes :  
  
-   Pour en savoir plus sur la personnalisation du ruban d'un élément Outlook, consultez [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## Voir aussi  
 [Accès à une zone de formulaire au moment de l'exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Directives pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procédure pas à pas : importation d'une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Association d'une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Comment : empêcher Outlook d'afficher une zone de formulaire](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  