---
title: Prise en main de la programmation des personnalisations au niveau du document pour Word
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
ms.openlocfilehash: 2b2872ca6496444cbb3878dc39800a8661400a76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62971795"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Prise en main de la programmation des personnalisations au niveau du document pour Word
  Si vous venez de commencer à créer des personnalisations au niveau du document pour Microsoft Office Word à l’aide de Visual Studio, voici ce que vous devez savoir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Comprendre le fonctionnement des personnalisations au niveau du document pour Word
 Chaque personnalisation de Word créée est basée sur un document unique. Pour commencer à utiliser la personnalisation, l’utilisateur final ouvre le document ou crée le document à partir d’un modèle Word. Les événements dans le document, par exemple en déplaçant le curseur dans des zones spécifiques ou en cliquant sur des boutons et des éléments de menu, peuvent appeler des méthodes de gestion d’événements dans l’assembly. Lorsque le document est fermé, les fonctionnalités fournies par la personnalisation ne sont plus disponibles dans Word.

 Pour plus d’informations, consultez [architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Créer des projets au niveau du document pour Word
 Pour créer une personnalisation au niveau du document pour Word, utilisez le modèle de projet de document Word ou de modèle Word dans la boîte de dialogue **nouveau projet** . Ces modèles comprennent les références d'assembly et les fichiers projet requis.

 Pour plus d’informations sur la création d’un projet au niveau du document pour Word, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programmer des documents Word à l’aide de contrôles hôtes d’éléments hôtes
 Les *éléments hôtes* et les *contrôles hôtes* sont des classes qui fournissent le modèle de programmation pour les personnalisations au niveau du document.

 Les éléments hôtes fournissent un point d’entrée pour votre code et peuvent également servir de conteneurs pour les contrôles hôtes et les contrôles de Windows Forms. Dans les projets au niveau du document pour Word, l’élément hôte est représenté par la `ThisDocument` classe.

 Les contrôles hôtes sont basés sur des objets Word natifs, tels que les contrôles de contenu, les signets et les nœuds XML. Les contrôles hôtes offrent des fonctionnalités similaires aux objets Word natifs, mais ils disposent également de nouveaux événements, de la prise en charge du concepteur et de la fonctionnalité de liaison de données. Elles apparaissent en tant qu’objets de première classe dans votre code de projet et dans IntelliSense, ce qui facilite la référence à des objets spécifiques directement dans votre code sans avoir à naviguer dans le modèle objet Word.

 Pour plus d'informations, voir les rubriques suivantes :

- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)

- [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)

- [Vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Personnaliser l’interface utilisateur de Word
 La plupart des solutions Microsoft Officees modifient l’interface utilisateur de l’application Office pour offrir aux utilisateurs un moyen d’interagir avec la solution. Vous pouvez modifier l’interface utilisateur de Word à l’aide d’une personnalisation au niveau du document de plusieurs façons. Par exemple, vous pouvez ajouter des contrôles au ruban, et vous pouvez afficher un volet Actions. Pour plus d’informations, consultez [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md).

 Vous pouvez également ouvrir le document associé à votre projet directement dans Visual Studio. Lorsque le document est ouvert dans Visual Studio, vous pouvez modifier le document à l’aide de l’interface utilisateur de Word. Vous pouvez également utiliser le document comme une aire de conception, ce qui vous permet de faire glisser des contrôles sur celui-ci. Pour plus d’informations, consultez [projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Lier des contrôles à des données
 Les contrôles de contenu et le <xref:Microsoft.Office.Tools.Word.Bookmark> contrôle figurent dans la liste des contrôles que vous pouvez faire glisser à partir de la fenêtre **sources de données** . L’ajout de contrôles de contenu et de signets de cette manière les lie automatiquement à la source de données que vous avez configurée à l’aide de la fenêtre. Sans écrire de code, vous pouvez afficher des données à partir des bases de données, des services et des objets métier. Pour plus d’informations, consultez [lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Étapes suivantes
 Pour savoir comment créer une personnalisation au niveau du document pour Word, consultez [procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Cette procédure pas à pas vous présente les outils de développement Office dans Visual Studio et le modèle de programmation pour les personnalisations au niveau du document Word.

 Pour obtenir la liste des rubriques qui vous guident à travers certaines des tâches courantes dans les projets Word, consultez [tâches courantes dans la programmation Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)
- [solutions Word](../vsto/word-solutions.md)
- [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)
- [Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)
- [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)
