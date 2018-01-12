---
title: "Utilisation de contrôles WPF dans les Solutions Office | Documents Microsoft"
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
helpviewer_keywords: WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 74ee8c574f6f654aca166844d85a30f2d3d9d4c3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="using-wpf-controls-in-office-solutions"></a>Utilisation de contrôles WPF dans les solutions Office
  Bien que les solutions créées à l'aide des outils de développement Office dans Visual Studio soient conçues pour fonctionner directement avec les contrôles Windows Forms, vous pouvez également utiliser des contrôles WPF dans vos solutions. Windows Presentation Foundation (WPF) est une alternative à Windows Forms pour concevoir des interfaces utilisateur. WPF utilise un langage de balisage appelé XAML (eXtensible Application Markup Language) qui offre de nouvelles techniques pour intégrer l'interface utilisateur, les médias et les documents. Pour plus d’informations, consultez [présentation de WPF dans Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Tout élément d'interface utilisateur qui peut héberger des contrôles Windows Forms dans une solution Office peut également héberger des contrôles WPF. Ces éléments sont entre autres les suivants :  
  
-   Les documents et les feuilles de calcul dans les personnalisations au niveau du document.  
  
-   Les volets Actions dans les personnalisations au niveau du document.  
  
-   Les volets de tâches personnalisés dans les compléments VSTO.  
  
-   Les zones de formulaire dans les compléments VSTO pour Outlook.  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>Ajout de contrôles WPF aux projets Office au moment du design  
 Vous ne pouvez pas ajouter des contrôles WPF directement aux éléments d'interface utilisateur dans les solutions Office. À la place, ajoutez un **contrôle utilisateur (WPF)** d’élément à votre projet et utilisez-le comme aire de conception pour les contrôles WPF. Puis, ajoutez le contrôle utilisateur WPF à un élément d'interface utilisateur de votre projet.  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Pour ajouter des contrôles WPF à un volet Actions, un volet des tâches personnalisé ou une zone de formulaire  
  
1.  Ouvrez un projet auquel vous souhaitez ajouter un volet des tâches personnalisé, un volet Actions ou une zone de formulaire.  
  
2.  Ajouter un **contrôle utilisateur (WPF)** élément à votre projet.  
  
3.  À partir de la **boîte à outils**, ajouter des contrôles WPF à l’aire de conception de contrôles utilisateur WPF.  
  
     Par défaut, lorsque le Concepteur de contrôles utilisateur WPF est ouvert, le **boîte à outils** contient uniquement des contrôles WPF.  
  
4.  Générez le projet.  
  
5.  Ajoutez un volet Actions, une zone de formulaire ou un volet des tâches personnalisé à votre projet :  
  
    -   Pour les zones de formulaire, ajoutez un **zone de formulaire Outlook** élément au projet. Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Pour les volets actions, ajoutez un **contrôle de volet Actions** ou **contrôle utilisateur** élément au projet. Pour plus d’informations, consultez [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) et [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Pour les volets de tâches personnalisés, ajoutez un **contrôle utilisateur** élément au projet. Pour plus d’informations, consultez [Comment : ajouter un volet de tâches personnalisé à une Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  À partir de la *nom_projet* **contrôles utilisateur WPF** onglet de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur pour le volet actions, une zone de formulaire ou un volet Office personnalisé.  
  
     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF sur l'élément d'interface utilisateur.  
  
7.  Regénérez le projet.  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Pour ajouter des contrôles WPF à un document ou à une feuille de calcul d'un projet au niveau du document  
  
1.  Ouvrez un projet au niveau du document pour Word ou Excel.  
  
2.  Ajouter un **contrôle utilisateur (WPF)** élément à votre projet.  
  
3.  À partir de la **boîte à outils**, ajouter des contrôles WPF à l’aire de conception de contrôles utilisateur WPF.  
  
4.  Générez le projet.  
  
5.  Ajouter un **contrôle utilisateur** élément (autrement dit, un contrôle utilisateur Windows Forms) au projet.  
  
6.  Ouvrez le concepteur pour le contrôle utilisateur Windows Forms.  
  
7.  À partir de la *nom_projet* **contrôles utilisateur WPF** onglet de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur.  
  
     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF dans le contrôle utilisateur Windows Forms.  
  
8.  Écrivez le code qui ajoute par programmation le contrôle utilisateur Windows Forms au document ou au classeur. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Vous ne pouvez pas faire glisser le contrôle utilisateur Windows Forms vers le document ou la feuille de calcul du concepteur .  
  
9. Regénérez le projet.  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>Hébergement des contrôles WPF à l'aide de la classe ElementHost  
 Visual Studio fournit des fonctionnalités qui vous aident à utiliser les contrôles Windows Forms dans vos solutions Office, mais il ne fournit pas de fonctionnalités similaires pour les contrôles WPF. Par exemple, vous pouvez ajouter des contrôles Windows Forms aux documents et feuilles de calcul au moment du design en faisant glisser des contrôles à partir de la **boîte à outils**, ou en cours d’exécution à l’aide des méthodes d’assistance. Cependant, ces outils ne sont pas disponibles pour les contrôles WPF.  
  
 Les contrôles WPF utilisent la classe <xref:System.Windows.Forms.Integration.ElementHost> comme couche d'intégration entre un formulaire ou contrôle Windows Forms et les contrôles WPF. Lorsque vous ajoutez des contrôles WPF à votre solution au moment du design, Visual Studio génère automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## <a name="wpf-resources"></a>Ressources WPF  
 Pour plus d'informations sur les problèmes d'architecture ou de conception d'hébergement des contrôles WPF sur les formulaires et les contrôles Windows Forms, consultez les rubriques suivantes :  
  
-   [Architecture d’entrée pour l’interopérabilité entre Windows Forms et WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Mappage de propriétés Windows Forms et WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Interopérabilité WPF et Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Contrôles Windows Forms et contrôles WPF équivalents](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Pour plus d'informations sur l'ajout de contrôles WPF à des formulaires et contrôles Windows Forms dans Visual Studio au moment du design, consultez les rubriques suivantes :  
  
-   [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Procédure pas à pas : application de styles au contenu WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Contrôles Windows Forms dans une vue d’ensemble des Documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)   
 [Volets de tâches personnalisés](../vsto/custom-task-panes.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Comment : ajouter un volet Actions à des Documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Comment : ajouter un volet Office personnalisé à une Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Guide pratique pour ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  