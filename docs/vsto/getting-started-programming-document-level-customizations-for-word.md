---
title: Prise en main de programmation des personnalisations au niveau du Document pour Word | Documents Microsoft
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
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 12265c725480324c396d59d848e5269432bb5d6e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-programming-document-level-customizations-for-word"></a>Mise en route de la programmation des personnalisations au niveau du document pour Word
  Si vous êtes novice dans la création de personnalisations au niveau du document pour Microsoft Office Word à l’aide de Visual Studio, voici ce que vous devez savoir.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-word-work"></a>Comprendre les personnalisations comment au niveau du Document pour Word  
 Chaque personnalisation Word que vous créez est basée sur un document unique. Pour démarrer à l’aide de la personnalisation, l’utilisateur final ouvre le document ou crée le document à partir d’un modèle Word. Certains événements dans le document, par exemple déplacement du curseur dans des zones spécifiques ou en cliquant sur les boutons et des éléments de menu, peuvent appeler des méthodes de gestion des événements dans l’assembly. Lorsque le document est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Word.  
  
 Pour plus d’informations, consultez [Architecture des personnalisations de niveau Document](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-word"></a>Création de projets de niveau Document pour Word  
 Pour créer une personnalisation au niveau du document pour Word, utilisez le modèle de projet Document Word ou de modèle Word dans le **nouveau projet** boîte de dialogue. Ces modèles comprennent les références d'assembly et les fichiers projet requis.  
  
 Pour plus d’informations sur la création d’un projet au niveau du document pour Word, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-word-documents-by-using-host-items-host-controls"></a>Programmation de Documents Word à l’aide de contrôles de hôte d’éléments hôtes  
 *Éléments hôtes* et *contrôles hôtes* sont des classes qui fournissent le modèle de programmation des personnalisations au niveau du document.  
  
 Les éléments hôtes fournissent un point d’entrée pour votre code, et ils peuvent également fonctionner comme conteneurs pour les contrôles hôtes et des contrôles Windows Forms. Dans les projets au niveau du document pour Word, l’élément hôte est représenté par la `ThisDocument` classe.  
  
 Contrôles hôtes sont basées sur des objets Word natifs, tels que les contrôles de contenu, les signets et les nœuds XML. Contrôles hôtes fournissent des fonctionnalités semblables aux objets Word natifs, mais ils possèdent également des nouveaux événements, un support concepteur et des fonctions de liaison de données. Ils apparaissent en tant qu’objets de première classe dans votre code de projet et dans IntelliSense, ce qui le rend plus facile de faire référence à des objets spécifiques directement dans votre code sans devoir parcourir le modèle objet Word.  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-word"></a>Personnalisation de l'interface utilisateur de Word  
 La plupart des solutions Microsoft Office modifient l’interface utilisateur (IU) de l’application Office pour permettre aux utilisateurs d’interagir avec la solution. Il existe plusieurs façons dans laquelle vous pouvez modifier l’interface utilisateur de Word à l’aide d’une personnalisation au niveau du document. Par exemple, vous pouvez ajouter des contrôles au ruban, et vous pouvez afficher un volet actions. Pour plus d’informations, consultez [personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).  
  
 Vous pouvez également ouvrir le document associé à votre projet directement dans Visual Studio. Lorsque le document est ouvert dans Visual Studio, vous pouvez modifier le document à l’aide de l’interface utilisateur de Word. Vous pouvez également utiliser le document comme une aire de conception, ce qui vous permet de faire glisser des contrôles sur lui. Pour plus d’informations, consultez [les projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="binding-controls-to-data"></a>Liaison de contrôles à des données  
 Les contrôles de contenu et le <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle se trouvent dans la liste des contrôles que vous pouvez faire glisser à partir de la **des Sources de données** fenêtre. Ajout de contrôles de contenu et signets de cette façon automatiquement les lie à la source de données que vous avez configurée à l’aide de la fenêtre. Sans écrire de code, vous pouvez afficher des données à partir de bases de données, des services et des objets métier. Pour plus d’informations, consultez [liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour savoir comment créer une personnalisation au niveau du document pour Word, consultez [procédure pas à pas : création de votre premier au niveau du Document personnalisation pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Cette procédure pas à pas vous présente les outils de développement Office dans Visual Studio et le modèle de programmation pour les personnalisations au niveau du document Word.  
  
 Pour obtenir la liste des rubriques vous présentant certaines des tâches courantes dans les projets Word, consultez [tâches courantes en matière de programmation Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmation des personnalisations au niveau du Document](../vsto/programming-document-level-customizations.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Procédure pas à pas : Création de votre première personnalisation au niveau du Document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)   
 [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  