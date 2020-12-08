---
title: 'Excel : prise en main de la programmation des personnalisations au niveau du document'
description: Découvrez ce que vous devez savoir pour commencer à créer des personnalisations au niveau du document pour Microsoft Office Excel à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fb048fd015126e5438a007be1950cddffbac9e1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846036"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Prise en main de la programmation des personnalisations au niveau du document pour Excel
  Si vous venez de commencer à créer des personnalisations au niveau du document pour Microsoft Office Excel à l’aide de Visual Studio, voici ce que vous devez savoir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Comprendre le fonctionnement des personnalisations au niveau du document pour Excel
 Une personnalisation au niveau du document pour Excel est basée sur un classeur unique. Pour commencer à utiliser la personnalisation, l’utilisateur final ouvre le classeur ou crée le classeur à partir d’un modèle Excel. Les événements dans le classeur, par exemple la saisie dans des cellules ou un clic sur les boutons et les éléments de menu, peuvent appeler des méthodes de gestion d’événements dans l’assembly. Lorsque le classeur est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Excel, uniquement dans le document qui les contient.

 Pour plus d’informations, consultez [architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Créer des projets au niveau du document pour Excel
 Pour créer une personnalisation au niveau du document pour Excel, utilisez le modèle de projet classeur Excel ou modèle Excel dans la boîte de dialogue **nouveau projet** . Ces modèles comprennent les références d'assembly et les fichiers projet requis.

 Pour plus d’informations sur la création d’un projet au niveau du document pour Excel, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmer des classeurs Excel à l’aide des éléments hôtes et des contrôles hôtes
 Les *éléments hôtes* et les *contrôles hôtes* sont des classes qui fournissent le modèle de programmation pour les personnalisations au niveau du document créées à l’aide de Visual Studio.

 Les éléments hôtes fournissent un point d’entrée pour votre code et peuvent également servir de conteneurs pour les contrôles hôtes et les contrôles de Windows Forms. Dans les projets au niveau du document pour Excel, ces éléments hôtes sont représentés par les `ThisWorkbook` classes,, `Sheet1` `Sheet2` et `Sheet3` .

 Les contrôles hôtes sont basés sur des objets Excel natifs, tels que des objets de liste et des plages. Les contrôles hôtes offrent des fonctionnalités similaires aux objets Excel natifs, mais ils disposent également de nouveaux événements, de la prise en charge du concepteur et de la fonctionnalité de liaison de données. Elles apparaissent en tant qu’objets de première classe dans votre code de projet et dans IntelliSense, ce qui facilite la référence à des objets spécifiques directement dans votre code sans avoir à naviguer dans le modèle objet Excel.

 Pour plus d'informations, voir les rubriques suivantes :

- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)

- [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)

- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Personnaliser l’interface utilisateur d’Excel
 La plupart des solutions Microsoft Officees modifient l’interface utilisateur de l’application Office pour offrir aux utilisateurs un moyen d’interagir avec la solution. Vous pouvez modifier l’interface utilisateur d’Excel de plusieurs manières à l’aide d’une personnalisation au niveau du document. Par exemple, vous pouvez ajouter des contrôles au ruban, ou vous pouvez afficher un volet Actions. Pour plus d’informations, consultez [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

 Vous pouvez également ouvrir le classeur qui est associé à votre projet directement dans Visual Studio. Lorsque le classeur est ouvert dans Visual Studio, vous pouvez modifier le classeur à l’aide de l’interface utilisateur d’Excel. Vous pouvez également utiliser le classeur comme une aire de conception, ce qui vous permet de faire glisser des contrôles sur des feuilles de calcul. Pour plus d’informations, consultez [projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Utiliser la liaison de données
 Les contrôles hôtes se trouvent également dans la liste des contrôles que vous pouvez faire glisser à partir de la fenêtre **sources de données** . L’ajout de contrôles hôtes de cette manière les lie automatiquement à la source de données que vous avez configurée à l’aide de la fenêtre. Sans écrire de code, vous pouvez afficher les données des bases de données, des services Web et des objets métier. Pour plus d’informations, consultez [lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Étapes suivantes
 Pour savoir comment créer une personnalisation au niveau du document pour Excel, consultez [procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Cette procédure pas à pas vous présente les outils de développement Office dans Visual Studio et le modèle de programmation pour les personnalisations au niveau du document Excel.

 Pour obtenir la liste des rubriques qui vous guident lors de certaines tâches courantes dans les projets Excel, consultez [tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [Solutions Excel](../vsto/excel-solutions.md)
- [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)
- [Vue d’ensemble du modèle objet Excel](../vsto/excel-object-model-overview.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
