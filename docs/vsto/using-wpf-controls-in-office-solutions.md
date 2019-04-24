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
ms.openlocfilehash: c8c447ce6b202fc3ccca65c6725e9eb3e5f13ecf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041527"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Utiliser des contrôles WPF dans les solutions Office

Bien que les solutions créées à l'aide des outils de développement Office dans Visual Studio soient conçues pour fonctionner directement avec les contrôles Windows Forms, vous pouvez également utiliser des contrôles WPF dans vos solutions. Windows Presentation Foundation (WPF) est une alternative à Windows Forms pour concevoir des interfaces utilisateur. WPF utilise un langage de balisage appelé XAML (eXtensible Application Markup Language) qui offre de nouvelles techniques pour intégrer l'interface utilisateur, les médias et les documents. Pour plus d’informations, consultez [vue d’ensemble WPF](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Tout élément d'interface utilisateur qui peut héberger des contrôles Windows Forms dans une solution Office peut également héberger des contrôles WPF. Ces éléments sont entre autres les suivants :

- Les documents et les feuilles de calcul dans les personnalisations au niveau du document.

- Les volets Actions dans les personnalisations au niveau du document.

- Les volets de tâches personnalisés dans les compléments VSTO.

- Les zones de formulaire dans les compléments VSTO pour Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Ajouter des contrôles WPF aux projets Office au moment du design

Vous ne pouvez pas ajouter des contrôles WPF directement aux éléments d'interface utilisateur dans les solutions Office. Au lieu de cela, ajoutez un **contrôle utilisateur (WPF)** d’élément à votre projet et utilisez-le comme aire de conception pour les contrôles WPF. Puis, ajoutez le contrôle utilisateur WPF à un élément d'interface utilisateur de votre projet.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Pour ajouter des contrôles WPF à un volet Actions, un volet des tâches personnalisé ou une zone de formulaire

1. Ouvrez un projet auquel vous souhaitez ajouter un volet des tâches personnalisé, un volet Actions ou une zone de formulaire.

2. Ajouter un **contrôle utilisateur (WPF)** élément à votre projet.

3. À partir de la **boîte à outils**, ajouter des contrôles WPF à l’aire de conception de contrôle utilisateur WPF.

     Par défaut, lorsque le Concepteur de contrôles utilisateur WPF est ouvert, le **boîte à outils** contient uniquement des contrôles WPF.

4. Générez le projet.

5. Ajoutez un volet Actions, une zone de formulaire ou un volet des tâches personnalisé à votre projet :

    - Pour les zones de formulaire, ajoutez un **zone de formulaire Outlook** élément au projet. Pour plus d'informations, voir [Procédure : Ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Pour les volets actions, ajoutez un **contrôle de volet Actions** ou **contrôle utilisateur** élément au projet. Pour plus d'informations, voir [Procédure : Ajouter un volet actions à des documents Word ou de classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) et [Comment : Ajouter un volet actions à des documents Word ou de classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - Pour les volets de tâches personnalisés, ajoutez un **contrôle utilisateur** élément au projet. Pour plus d'informations, voir [Procédure : Ajouter un volet Office personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. À partir de la *nom_projet* **contrôles utilisateur WPF** onglet de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur pour le volet actions, une zone de formulaire ou un volet Office personnalisé.

     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF sur l'élément d'interface utilisateur.

7. Regénérez le projet.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Pour ajouter des contrôles WPF à un document ou à une feuille de calcul d'un projet au niveau du document

1. Ouvrez un projet au niveau du document pour Word ou Excel.

2. Ajouter un **contrôle utilisateur (WPF)** élément à votre projet.

3. À partir de la **boîte à outils**, ajouter des contrôles WPF à l’aire de conception de contrôle utilisateur WPF.

4. Générez le projet.

5. Ajouter un **contrôle utilisateur** élément (autrement dit, un contrôle utilisateur Windows Forms) au projet.

6. Ouvrez le concepteur pour le contrôle utilisateur Windows Forms.

7. À partir de la *nom_projet* **contrôles utilisateur WPF** onglet de la **boîte à outils**, faites glisser le contrôle utilisateur WPF vers le concepteur.

     Visual Studio crée automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost> qui héberge le contrôle utilisateur WPF dans le contrôle utilisateur Windows Forms.

8. Écrivez le code qui ajoute par programmation le contrôle utilisateur Windows Forms au document ou au classeur. Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Vous ne pouvez pas faire glisser le contrôle utilisateur Windows Forms vers le document ou la feuille de calcul du concepteur .

9. Regénérez le projet.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Héberger des contrôles WPF à l’aide de la classe ElementHost

Visual Studio fournit des fonctionnalités qui vous aident à utiliser les contrôles Windows Forms dans vos solutions Office, mais il ne fournit pas de fonctionnalités similaires pour les contrôles WPF. Par exemple, vous pouvez ajouter des contrôles Windows Forms aux documents et feuilles de calcul au moment du design en faisant glisser des contrôles à partir de la **boîte à outils**, ou lors de l’exécution à l’aide des méthodes d’assistance. Cependant, ces outils ne sont pas disponibles pour les contrôles WPF.

Les contrôles WPF utilisent la classe <xref:System.Windows.Forms.Integration.ElementHost> comme couche d'intégration entre un formulaire ou contrôle Windows Forms et les contrôles WPF. Lorsque vous ajoutez des contrôles WPF à votre solution au moment du design, Visual Studio génère automatiquement un objet <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Ressources WPF

Pour plus d'informations sur les problèmes d'architecture ou de conception d'hébergement des contrôles WPF sur les formulaires et les contrôles Windows Forms, consultez les rubriques suivantes :

- [Architecture de d’entrée de l’interopérabilité entre Windows Forms et WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Mappage de propriété Windows Forms et WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Interopérabilité WPF et Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Contrôles Windows Forms et contrôles WPF équivalents](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Pour plus d'informations sur l'ajout de contrôles WPF à des formulaires et contrôles Windows Forms dans Visual Studio au moment du design, consultez les rubriques suivantes :

- [Procédure pas à pas : Créer du contenu WPF dans les Windows Forms au moment du design](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Procédure pas à pas : Organiser le contenu WPF sur les Windows Forms au moment du design](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Procédure pas à pas : Contenu WPF de style](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Voir aussi

- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
- [Contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)
- [Volets Office personnalisés](../vsto/custom-task-panes.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Guide pratique pour Ajouter un volet actions à des documents Word ou des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Guide pratique pour Ajouter un volet Office personnalisé à une application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Guide pratique pour Ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
