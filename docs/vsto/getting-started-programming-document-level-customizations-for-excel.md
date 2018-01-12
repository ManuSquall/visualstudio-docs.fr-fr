---
title: Prise en main de programmation des personnalisations au niveau du Document pour Excel | Documents Microsoft
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
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fdf4afeb260d94b9e121628163c760244ac5f6e1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Mise en route de la programmation des personnalisations au niveau du document pour Excel
  Si vous êtes novice dans la création de personnalisations au niveau du document pour Microsoft Office Excel à l’aide de Visual Studio, voici ce que vous devez savoir.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>Comprendre les personnalisations comment au niveau du Document pour Excel  
 Une personnalisation au niveau du document pour Excel est basée sur un classeur unique. Pour démarrer à l’aide de la personnalisation, l’utilisateur final ouvre le classeur ou crée le classeur à partir d’un modèle Excel. Certains événements dans le classeur, par exemple en tapant dans des cellules ou en cliquant sur les boutons et des éléments de menu, peuvent appeler des méthodes de gestion des événements dans l’assembly. Lorsque le classeur est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Excel, uniquement dans le document les contenant.  
  
 Pour plus d’informations, consultez [Architecture des personnalisations de niveau Document](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-excel"></a>Création de projets de niveau Document pour Excel  
 Pour créer une personnalisation au niveau du document pour Excel, utilisez le modèle de projet de classeur Excel ou modèle Excel dans le **nouveau projet** boîte de dialogue. Ces modèles comprennent les références d'assembly et les fichiers projet requis.  
  
 Pour plus d’informations sur la création d’un projet au niveau du document pour Excel, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmation de classeurs Excel à l’aide des éléments hôtes et des contrôles hôtes  
 *Éléments hôtes* et *contrôles hôtes* sont des classes qui fournissent le modèle de programmation pour les personnalisations au niveau du document créées à l’aide de Visual Studio.  
  
 Les éléments hôtes fournissent un point d’entrée pour votre code, et ils peuvent également fonctionner comme conteneurs pour les contrôles hôtes et des contrôles Windows Forms. Dans les projets au niveau du document pour Excel, ces éléments hôtes sont représentés par le `ThisWorkbook`, `Sheet1`, `Sheet2`, et `Sheet3` classes.  
  
 Contrôles hôtes sont basées sur des objets Excel natifs, tels que les objets de liste et les plages. Contrôles hôtes fournissent des fonctionnalités semblables aux objets Excel natifs, mais ils possèdent également des nouveaux événements prise en charge de concepteur et la fonctionnalité de liaison de données. Ils apparaissent en tant qu’objets de première classe dans votre code de projet et dans IntelliSense, ce qui le rend plus facile de faire référence à des objets spécifiques directement dans votre code sans devoir parcourir le modèle objet Excel.  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>Personnalisation de l'interface utilisateur d'Excel  
 La plupart des solutions Microsoft Office modifient l’interface utilisateur (IU) de l’application Office pour permettre aux utilisateurs d’interagir avec la solution. Il existe plusieurs façons dans laquelle vous pouvez modifier l’interface utilisateur d’Excel à l’aide d’une personnalisation au niveau du document. Par exemple, vous pouvez ajouter des contrôles au ruban, ou vous pouvez afficher un volet actions. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
 Vous pouvez également ouvrir le classeur associé à votre projet directement dans Visual Studio. Lorsque le classeur est ouvert dans Visual Studio, vous pouvez modifier le classeur à l’aide de l’interface utilisateur Excel. Vous pouvez également utiliser le classeur comme une aire de conception, ce qui vous permet de faire glisser des contrôles sur des feuilles de calcul. Pour plus d’informations, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="using-data-binding"></a>À l’aide de la liaison de données  
 Les contrôles hôtes sont également dans la liste des contrôles que vous pouvez faire glisser à partir de la **des Sources de données** fenêtre. Ajout de contrôles hôtes de cette façon automatiquement les lie à la source de données que vous avez configurée à l’aide de la fenêtre. Sans écrire de code, vous pouvez afficher les données des bases de données, des services web et des objets métier. Pour plus d’informations, consultez [liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour savoir comment créer une personnalisation au niveau du document pour Excel, consultez [procédure pas à pas : création de votre première personnalisation d’au niveau du Document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Cette procédure pas à pas vous présente les outils de développement Office dans Visual Studio et le modèle de programmation pour les personnalisations au niveau du document Excel.  
  
 Pour obtenir la liste des rubriques vous présentant certaines des tâches courantes dans les projets Excel, consultez [tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation des personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md)   
 [Solutions Excel](../vsto/excel-solutions.md)   
 [Procédure pas à pas : Création de votre première personnalisation au niveau du Document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)   
 [Vue d’ensemble du modèle d’objet Excel](../vsto/excel-object-model-overview.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  