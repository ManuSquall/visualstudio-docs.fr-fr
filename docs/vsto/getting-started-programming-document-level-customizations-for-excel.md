---
title: Prise en main de programmation de personnalisations au niveau du document pour Excel
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
ms.openlocfilehash: 47762c781b24a31b90c75e5f8d9f0d00a6d3363d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870137"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Prise en main de programmation de personnalisations au niveau du document pour Excel
  Si vous êtes novice dans la création de personnalisations au niveau du document pour Microsoft Office Excel à l’aide de Visual Studio, voici ce que vous devez savoir.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Comprendre des personnalisations comment au niveau du document pour Excel  
 Une personnalisation au niveau du document pour Excel est basée sur un classeur unique. Pour commencer à utiliser la personnalisation, l’utilisateur final ouvre le classeur ou crée le classeur à partir d’un modèle Excel. Événements dans le classeur, par exemple en tapant dans des cellules ou en cliquant sur les boutons et les éléments de menu, peuvent appeler des méthodes de gestion des événements dans l’assembly. Lorsque le classeur est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Excel, uniquement dans le document les contenant.  
  
 Pour plus d’informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Créer des projets de niveau document pour Excel  
 Pour créer une personnalisation au niveau du document pour Excel, utilisez le modèle de projet de classeur Excel ou modèle Excel dans le **nouveau projet** boîte de dialogue. Ces modèles comprennent les références d'assembly et les fichiers projet requis.  
  
 Pour plus d’informations sur la création d’un projet au niveau du document pour Excel, consultez [Comment : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmer des classeurs Excel à l’aide des éléments hôtes et contrôles hôtes  
 *Éléments hôtes* et *contrôles hôtes* sont des classes qui fournissent le modèle de programmation pour les personnalisations au niveau du document créées à l’aide de Visual Studio.  
  
 Éléments hôtes fournissent un point d’entrée pour votre code, et ils peuvent également agir en tant que conteneurs pour les contrôles hôtes et contrôles Windows Forms. Dans les projets au niveau du document pour Excel, ces éléments hôtes sont représentés par le `ThisWorkbook`, `Sheet1`, `Sheet2`, et `Sheet3` classes.  
  
 Contrôles hôtes sont basées sur des objets Excel natifs, tels que les objets de liste et les plages. Contrôles hôtes fournissent des fonctionnalités similaires pour les objets Excel natifs, mais ils ont également les nouveaux événements concepteur prise en charge et la fonctionnalité de liaison de données. Ils apparaissent comme des objets de première classe dans votre code de projet et dans IntelliSense, ce qui le rend plus facile faire référence à des objets spécifiques directement dans votre code sans avoir à naviguer dans le modèle objet Excel.  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)  
  
-   [Automatiser Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Personnaliser l’interface utilisateur d’Excel  
 La plupart des solutions Microsoft Office Modifier l’interface utilisateur (IU) de l’application Office pour fournir aux utilisateurs d’interagir avec la solution. Il existe plusieurs façons dans laquelle vous pouvez modifier l’interface utilisateur d’Excel à l’aide d’une personnalisation au niveau du document. Par exemple, vous pouvez ajouter des contrôles au ruban, ou vous pouvez afficher un volet actions. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
 Vous pouvez également ouvrir le classeur associé à votre projet directement dans Visual Studio. Lorsque le classeur est ouvert dans Visual Studio, vous pouvez modifier le classeur à l’aide de l’interface utilisateur Excel. Vous pouvez également utiliser le classeur comme une aire de conception, ce qui vous permet de faire glisser des contrôles sur des feuilles de calcul. Pour plus d’informations, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Utiliser la liaison de données  
 Les contrôles hôtes sont également dans la liste des contrôles que vous pouvez faire glisser à partir de la **des Sources de données** fenêtre. Ajout de contrôles hôtes de cette façon automatiquement les lie à la source de données que vous avez configurés à l’aide de la fenêtre. Sans écrire de code, vous pouvez afficher des données à partir de bases de données, les services web et les objets métier. Pour plus d’informations, consultez [lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour savoir comment créer une personnalisation au niveau du document pour Excel, consultez [procédure pas à pas : Créer votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Cette procédure pas à pas vous présente les outils de développement Office dans Visual Studio et le modèle de programmation pour les personnalisations au niveau du document Excel.  
  
 Pour obtenir la liste des rubriques qui vous guident dans certaines des tâches courantes dans les projets Excel, consultez [tâches courantes dans la programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Procédure pas à pas : Créer votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
