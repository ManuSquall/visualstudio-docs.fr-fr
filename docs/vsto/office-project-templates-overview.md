---
title: Vue d’ensemble des modèles de projet Office
description: Découvrez comment les outils de développement Microsoft Office dans Visual Studio incluent des modèles de projet pour la création de différents types de solutions Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e3203eb4bbd7339f5e59ecffea8436b02180b8b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528074"
---
# <a name="office-project-templates-overview"></a>Vue d’ensemble des modèles de projet Office
  Les Outils de développement Microsoft Office dans Visual Studio incluent des modèles de projet pour la création des types suivants de solutions Office :

- [Personnalisations au niveau du document](#DocLevel)

- [Compléments VSTO](#AppLevel)

  Pour une comparaison détaillée de ces types de solutions Office, consultez [vue d’ensemble du développement des solutions office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

  Les modèles de projet Office sont disponibles dans la boîte de dialogue **Nouveau projet** , sous le nœud **Office** des nœuds de langage **Visual C#** et **Visual Basic** . Chaque modèle génère un projet avec la configuration appropriée pour l'application cible, y compris les références d'assembly et les paramètres de débogage.

  Chaque projet fournit des fichiers et du code qui vous aident à démarrer sur un genre de solution spécifique. Le code généré pour chaque projet inclut le démarrage et l'arrêt des gestionnaires d'événements. Vous pouvez ajouter du code à ces gestionnaires pour initialiser votre solution lorsqu'elle est chargée et pour la nettoyer lorsqu'elle est déchargée. Pour plus d’informations, consultez [projets Office dans l’environnement Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) et [événements dans les projets Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> Les Outils de développement Office sont inclus avec certaines éditions de Visual Studio. Pour plus d’informations, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Personnalisations au niveau du document
 Le nœud **Office** dans la boîte de dialogue **Nouveau projet** fournit les modèles de projet suivants pour vous aider à créer des personnalisations au niveau du document pour Word et Excel :

- **Document VSTO pour Word 2013 et 2016**

- **Modèle VSTO pour Word 2013 et 2016**

- **Classeur VSTO pour Excel 2013 et 2016**

- **Modèle VSTO pour Excel 2013 et 2016**

- **Document VSTO pour Word 2010**

- **Modèle VSTO pour Word 2010**

- **Classeur VSTO pour Excel 2010**

- **Modèle VSTO pour Excel 2010**

  Les modèles de projet Document Word et Classeur Excel fournissent le code qui vous permet de commencer à créer une solution basée sur un document ou classeur spécifique. Dans ces types de solutions, votre code s'exécute uniquement lorsque le document associé est ouvert dans Word ou Excel.

  Les modèles de projet Modèle Word et Modèle Excel se comportent de la même façon que les modèles Document Word et Classeur Excel. Toutefois, les modèles de projet Modèle Word et Modèle Excel permettent aux utilisateurs de créer facilement un document local ou des copies de classeur du modèle personnalisé dans votre solution. Les fonctionnalités de votre solution sont disponibles dans le nouveau document que l'utilisateur crée à partir du modèle.

> [!NOTE]
> Les modèles Word qui font référence à des extensions de code managé ne peuvent pas être utilisés comme compléments VSTO globaux. L’assembly n’est pas appelé si le modèle est chargé à partir du répertoire de démarrage de Word. Pour plus d’informations, consultez [limitations des modèles globaux et des compléments Excel (fichiers. xla)](#Limitations).

 Pour plus d'informations sur la mise en route avec ces types de projet, consultez les rubriques suivantes :

- [Personnaliser les personnalisations au niveau du document](../vsto/programming-document-level-customizations.md)

- [Solutions Word](../vsto/word-solutions.md)

- [Solutions Excel](../vsto/excel-solutions.md)

- [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a> Compléments VSTO
 Le nœud **Office/SharePoint** dans la boîte de dialogue **Nouveau projet** fournit les modèles de projets suivants pour vous aider à créer des compléments VSTO.

- **Complément VSTO pour Excel 2013 et 2016**

- **Complément VSTO pour InfoPath 2013**

- **Complément VSTO pour Outlook 2013 et 2016**

- **Complément VSTO pour PowerPoint 2013 et 2016**

- **Complément pour Project 2013 et 2016**

- **Complément pour Visio 2013 et 2016**

- **Complément pour Word 2013 et 2016**

- **Complément pour Excel 2010**

- **Complément pour InfoPath 2010**

- **Complément pour Outlook 2010**

- **Complément pour PowerPoint 2010**

- **Complément pour Project 2010**

- **Complément pour Visio 2010**

- **Complément pour Word 2010**

  Lorsque vous créez un projet basé sur l'un de ces modèles de projet, le code de votre solution s'exécute lorsque l'application associée est ouverte. Contrairement aux projets au niveau du document, le code n'est pas associé à un document unique.

  Pour plus d'informations sur la mise en route avec ces types de projet, consultez les rubriques suivantes :

- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Programmer les compléments VSTO](../vsto/programming-vsto-add-ins.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Procédure pas à pas : créer votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Solutions de documents et de modèles
 Lorsque vous concevez une solution basée sur un document Word ou un classeur Excel, vous devez déterminer la meilleure façon de rendre ce document accessible aux utilisateurs.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Dans certains cas, il est possible de donner une copie d'un document à chaque utilisateur. Dans ce cas, créez votre solution à l'aide d'un projet de document Excel ou Word.

 Dans d'autres cas, vous pouvez rendre un modèle disponible sur un serveur, de sorte que chaque utilisateur puisse l'ouvrir et enregistrer une copie locale sous forme de document. Dans ce cas, créez votre solution à l'aide d'un projet de modèle Excel ou Word.

## <a name="comparison"></a>Comparaison
 Le tableau suivant souligne les différences entre les documents et les modèles.

|Documents|Modèles|
|---------------|---------------|
|Les utilisateurs peuvent ouvrir et modifier un document, sauf s'il est en lecture seule. Les modifications enregistrées sont conservées dans l'original.|Les utilisateurs peuvent ouvrir un modèle pour créer une copie locale sous forme de nouveau document. Ils ne peuvent pas modifier l'original à moins qu'ils ne disposent d'autorisations particulières.|
|Une fois le document ouvert, il déclenche l'événement <xref:Microsoft.Office.Tools.Word.Document.Open> .|Une fois le modèle ouvert, il déclenche l'événement <xref:Microsoft.Office.Tools.Word.Document.New> .|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a> Limitations des modèles globaux et des compléments Excel (fichiers. xla)
 Les documents, classeurs et modèles peuvent ne pas fonctionner correctement en tant que modèles globaux ou compléments VSTO Excel (fichiers .xla).

## <a name="word-templates"></a>Modèles Word
 Si un modèle Microsoft Office Word a des extensions de code managé, l'assembly de projet n'est pas appelé si le modèle est attaché en tant que modèle global ou chargé à partir du répertoire de démarrage de Word. En outre, le document ne reconnaît pas le format d'un modèle faisant partie d'une solution Office.

## <a name="excel-add-ins-xla-files"></a>Compléments Excel (fichiers. xla)
 Il n’existe aucun projet Office pour créer un complément VSTO Excel (fichier *. xla* ). Il est possible d'enregistrer un classeur en tant que fichier .xla, mais cette opération, qui n'est pas prise en charge, n'est pas recommandée. Si vous enregistrez un classeur qui a des extensions de code managé sous la forme d’un fichier **Microsoft Office Excel Add-In ( \* . xla)** , vous pouvez le sélectionner dans la boîte de dialogue **compléments** pour l’appliquer à un autre classeur. Dans certains cas, votre code s’exécutera dans le classeur cible après l’application du complément VSTO, mais une telle utilisation de la solution Office n’est pas prise en charge.

## <a name="see-also"></a>Voir aussi
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Développer des solutions Office](../vsto/developing-office-solutions.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Prise en main de la programmation des personnalisations au niveau du document pour Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Prise en main de la programmation des personnalisations au niveau du document pour Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Prise en main de la programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
