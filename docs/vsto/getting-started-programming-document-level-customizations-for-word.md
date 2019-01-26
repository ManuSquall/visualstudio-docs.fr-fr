---
title: Prise en main de programmation de personnalisations au niveau du document pour Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b8ac2efc6627eae017c7154743091b7682dc8ac
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869198"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Prise en main de programmation de personnalisations au niveau du document pour Word
  Si vous êtes novice dans la création de personnalisations au niveau du document pour Microsoft Office Word à l’aide de Visual Studio, voici ce que vous devez savoir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Comprendre des personnalisations comment au niveau du document pour Word  
 Chaque personnalisation de Word que vous créez est basée sur un document unique. Pour commencer à utiliser la personnalisation, l’utilisateur final ouvre le document ou crée le document à partir d’un modèle Word. Événements dans le document, par exemple plaçant le curseur dans des zones spécifiques ou en cliquant sur les boutons et les éléments de menu, peuvent appeler des méthodes de gestion des événements dans l’assembly. Lorsque le document est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Word.  
  
 Pour plus d’informations, consultez [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Créer des projets de niveau document pour Word  
 Pour créer une personnalisation au niveau du document pour Word, utilisez le modèle de projet Document Word ou modèle Word dans le **nouveau projet** boîte de dialogue. Ces modèles comprennent les références d'assembly et les fichiers projet requis.  
  
 Pour plus d’informations sur la création d’un projet au niveau du document pour Word, consultez [Comment : Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Documents Word de programme à l’aide des éléments hôtes de contrôles hôtes  
 *Éléments hôtes* et *contrôles hôtes* sont des classes qui fournissent le modèle de programmation de personnalisations au niveau du document.  
  
 Éléments hôtes fournissent un point d’entrée pour votre code, et ils peuvent également agir en tant que conteneurs pour les contrôles hôtes et contrôles Windows Forms. Dans les projets au niveau du document pour Word, l’élément hôte est représenté par la `ThisDocument` classe.  
  
 Contrôles hôtes sont basées sur des objets Word natifs, tels que les contrôles de contenu, les signets et les nœuds XML. Contrôles hôtes fournissent des fonctionnalités similaires pour les objets Word natifs, mais ils ont également les nouveaux événements, support concepteur et des fonctions de liaison de données. Ils apparaissent comme des objets de première classe dans votre code de projet et dans IntelliSense, ce qui le rend plus facile faire référence à des objets spécifiques directement dans votre code sans avoir à naviguer dans le modèle d’objet de Word.  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)  
  
-   [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Personnaliser l’interface utilisateur de Word  
 La plupart des solutions Microsoft Office Modifier l’interface utilisateur (IU) de l’application Office pour fournir aux utilisateurs d’interagir avec la solution. Il existe plusieurs façons dans laquelle vous pouvez modifier l’interface utilisateur de Word à l’aide d’une personnalisation au niveau du document. Par exemple, vous pouvez ajouter des contrôles au ruban, et vous pouvez afficher un volet actions. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
 Vous pouvez également ouvrir le document associé à votre projet directement dans Visual Studio. Lorsque le document est ouvert dans Visual Studio, vous pouvez modifier le document à l’aide de l’interface utilisateur de Word. Vous pouvez également utiliser le document comme une aire de conception, ce qui vous permet de glisser des contrôles. Pour plus d’informations, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Lier des contrôles à des données  
 Les contrôles de contenu et le <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle sont dans la liste des contrôles que vous pouvez faire glisser à partir de la **des Sources de données** fenêtre. Ajout de contrôles de contenu et crée des signets de cette façon automatiquement les lie à la source de données que vous avez configurés à l’aide de la fenêtre. Sans écrire de code, vous pouvez afficher des données à partir de bases de données, des services et des objets métier. Pour plus d’informations, consultez [lier des données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour savoir comment créer une personnalisation au niveau du document pour Word, consultez [procédure pas à pas : Créer votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Cette procédure pas à pas vous présente les outils de développement Office dans Visual Studio et le modèle de programmation pour les personnalisations au niveau du document Word.  
  
 Pour obtenir la liste des rubriques qui vous guident dans certaines des tâches courantes dans les projets Word, consultez [tâches courantes dans la programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Procédure pas à pas : Créer votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)   
 [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
