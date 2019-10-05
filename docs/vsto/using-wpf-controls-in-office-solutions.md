---
title: Utiliser des contrôles WPF dans les solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0540ac17ca64f24ead19b8b3655175d12fa42e41
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253976"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Utiliser des contrôles WPF dans les solutions Office

Bien que les solutions créées à l'aide des outils de développement Office dans Visual Studio soient conçues pour fonctionner directement avec les contrôles Windows Forms, vous pouvez également utiliser des contrôles WPF dans vos solutions. Windows Presentation Foundation (WPF) est une alternative à Windows Forms pour concevoir des interfaces utilisateur. WPF utilise un langage de balisage appelé XAML (eXtensible Application Markup Language) qui offre de nouvelles techniques pour intégrer l'interface utilisateur, les médias et les documents. Pour plus d’informations, consultez [vue d’ensemble de WPF](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Tout élément d'interface utilisateur qui peut héberger des contrôles Windows Forms dans une solution Office peut également héberger des contrôles WPF. Ces éléments sont entre autres les suivants :

- Les documents et les feuilles de calcul dans les personnalisations au niveau du document.

- Les volets Actions dans les personnalisations au niveau du document.

- Les volets de tâches personnalisés dans les compléments VSTO.

- Les zones de formulaire dans les compléments VSTO pour Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Ajouter des contrôles WPF aux projets Office au moment du design

Vous ne pouvez pas ajouter des contrôles WPF directement aux éléments d'interface utilisateur dans les solutions Office. Au lieu de cela, ajoutez un élément de **contrôle utilisateur (WPF)** à votre projet et utilisez-le comme aire de conception pour les contrôles WPF. Puis, ajoutez le contrôle utilisateur WPF à un élément d'interface utilisateur de votre projet.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Pour ajouter des contrôles WPF à un volet Actions, un volet des tâches personnalisé ou une zone de formulaire

1. Ouvrez un projet auquel vous souhaitez ajouter un volet des tâches personnalisé, un volet Actions ou une zone de formulaire.

2. Ajoutez un élément de **contrôle utilisateur (WPF)** à votre projet.

3. À partir de la **boîte à outils**, ajoutez des contrôles WPF à l’aire de conception du contrôle utilisateur WPF.

     Par défaut, lorsque le concepteur de contrôles utilisateur WPF est ouvert, la **boîte à outils** contient uniquement des contrôles WPF.

4. Générez le projet.

5. Ajoutez un volet Actions, une zone de formulaire ou un volet des tâches personnalisé à votre projet :

    - Pour les zones de formulaire, ajoutez un élément de **zone de formulaire Outlook** au projet. Pour plus d'informations, voir [Procédure : Ajoutez une zone de formulaire à un projet](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)de complément Outlook.

    - Pour les volets actions, ajoutez un élément de contrôle de **volet Actions** ou un élément de **contrôle utilisateur** au projet. Pour plus d'informations, voir [Procédure : Ajoutez un volet actions à des documents Word ou à des](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)classeurs Excel.

    - Pour les volets des tâches personnalisés, ajoutez un élément de **contrôle utilisateur** au projet. Pour plus d'informations, voir [Procédure : Ajoutez un volet de tâches personnalisé à une](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)application.

6. À partir de l’onglet *NomProjet* **contrôles utilisateur WPF** de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur du volet Actions, de la zone de formulaire ou du volet Office personnalisé.

     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF sur l'élément d'interface utilisateur.

7. Regénérez le projet.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Pour ajouter des contrôles WPF à un document ou à une feuille de calcul d'un projet au niveau du document

1. Ouvrez un projet au niveau du document pour Word ou Excel.

2. Ajoutez un élément de **contrôle utilisateur (WPF)** à votre projet.

3. À partir de la **boîte à outils**, ajoutez des contrôles WPF à l’aire de conception du contrôle utilisateur WPF.

4. Générez le projet.

5. Ajoutez un élément de **contrôle utilisateur** (autrement dit, un contrôle utilisateur Windows Forms) au projet.

6. Ouvrez le concepteur pour le contrôle utilisateur Windows Forms.

7. À partir de l’onglet *NomProjet* **WPF User Controls** de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur.

     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF dans le contrôle utilisateur Windows Forms.

8. Écrivez le code qui ajoute par programmation le contrôle utilisateur Windows Forms au document ou au classeur. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Vous ne pouvez pas faire glisser le contrôle utilisateur Windows Forms vers le document ou la feuille de calcul du concepteur .

9. Regénérez le projet.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Héberger des contrôles WPF à l’aide de la classe ElementHost

Visual Studio fournit des fonctionnalités qui vous aident à utiliser les contrôles Windows Forms dans vos solutions Office, mais il ne fournit pas de fonctionnalités similaires pour les contrôles WPF. Par exemple, vous pouvez ajouter des contrôles Windows Forms aux documents et aux feuilles de calcul au moment du design en faisant glisser des contrôles à partir de la **boîte à outils**, ou au moment de l’exécution à l’aide des méthodes d’assistance. Cependant, ces outils ne sont pas disponibles pour les contrôles WPF.

Les contrôles WPF utilisent la classe <xref:System.Windows.Forms.Integration.ElementHost> comme couche d'intégration entre un formulaire ou contrôle Windows Forms et les contrôles WPF. Lorsque vous ajoutez des contrôles WPF à votre solution au moment du design, Visual Studio génère automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Ressources WPF

Pour plus d'informations sur les problèmes d'architecture ou de conception d'hébergement des contrôles WPF sur les formulaires et les contrôles Windows Forms, consultez les rubriques suivantes :

- [Architecture d’entrée de l’interopérabilité Windows Forms et WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Windows Forms et mappage des propriétés WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Interopérabilité entre WPF et Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Contrôles Windows Forms et contrôles WPF équivalents](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Pour plus d'informations sur l'ajout de contrôles WPF à des formulaires et contrôles Windows Forms dans Visual Studio au moment du design, consultez les rubriques suivantes :

- [Procédure pas à pas : Créer un contenu WPF sur Windows Forms au moment de la conception](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Procédure pas à pas : Organiser le contenu WPF sur Windows Forms au moment du design](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Procédure pas à pas : Contenu WPF du style](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Voir aussi

- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Vue d’ensemble des contrôles de Windows Forms sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Volets des tâches personnalisés](../vsto/custom-task-panes.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Guide pratique pour Ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Guide pratique pour Ajouter un volet de tâches personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Guide pratique pour Ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
