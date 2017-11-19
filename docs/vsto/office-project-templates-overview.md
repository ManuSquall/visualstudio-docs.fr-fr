---
title: "Vue d’ensemble des modèles de projet Office | Documents Microsoft"
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
ms.assetid: 2f86546b-307f-48ea-b01c-5f5a242fce17
caps.latest.revision: "68"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6066e5adbe4519011f56a4d88ecfcc834eb7788c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="office-project-templates-overview"></a>Vue d'ensemble des modèles de projet Office
  Les Outils de développement Microsoft Office dans Visual Studio incluent des modèles de projet pour la création des types suivants de solutions Office :  
  
-   [Personnalisations au niveau du document](#DocLevel)  
  
-   [Compléments VSTO](#AppLevel)  
  
 Pour une comparaison détaillée de ces types de solutions Office, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 Les modèles de projet Office sont disponibles dans la boîte de dialogue **Nouveau projet** , sous le nœud **Office** des nœuds de langage **Visual C#** et **Visual Basic** . Chaque modèle génère un projet avec la configuration appropriée pour l'application cible, y compris les références d'assembly et les paramètres de débogage.  
  
 Chaque projet fournit des fichiers et du code qui vous aident à démarrer sur un genre de solution spécifique. Le code généré pour chaque projet inclut le démarrage et l'arrêt des gestionnaires d'événements. Vous pouvez ajouter du code à ces gestionnaires pour initialiser votre solution lorsqu'elle est chargée et pour la nettoyer lorsqu'elle est déchargée. Pour plus d’informations, consultez [Office Projects in the Visual Studio Environment](../vsto/office-projects-in-the-visual-studio-environment.md) et [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Les Outils de développement Office sont inclus avec certaines éditions de Visual Studio. Pour plus d'informations, consultez [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
##  <a name="DocLevel"></a> Document-Level Customizations  
 Le nœud **Office** dans la boîte de dialogue **Nouveau projet** fournit les modèles de projet suivants pour vous aider à créer des personnalisations au niveau du document pour Word et Excel :  
  
-   **Document VSTO pour Word 2013 et 2016**  
  
-   **Modèle VSTO pour Word 2013 et 2016**  
  
-   **Classeur VSTO pour Excel 2013 et 2016**  
  
-   **Modèle VSTO pour Excel 2013 et 2016**  
  
-   **Document VSTO pour Word 2010**  
  
-   **Modèle VSTO pour Word 2010**  
  
-   **Classeur VSTO pour Excel 2010**  
  
-   **Modèle VSTO pour Excel 2010**  
  
 Les modèles de projet Document Word et Classeur Excel fournissent le code qui vous permet de commencer à créer une solution basée sur un document ou classeur spécifique. Dans ces types de solutions, votre code s'exécute uniquement lorsque le document associé est ouvert dans Word ou Excel.  
  
 Les modèles de projet Modèle Word et Modèle Excel se comportent de la même façon que les modèles Document Word et Classeur Excel. Toutefois, les modèles de projet Modèle Word et Modèle Excel permettent aux utilisateurs de créer facilement un document local ou des copies de classeur du modèle personnalisé dans votre solution. Les fonctionnalités de votre solution sont disponibles dans le nouveau document que l'utilisateur crée à partir du modèle.  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser des modèles Word qui font référence à des extensions de code managé comme compléments VSTO globaux. L'assembly n'est pas appelé si le modèle est chargé à partir du répertoire Startup de Word. Pour plus d'informations, consultez [Limitations des modèles globaux et des compléments Excel (fichiers .xla)](#Limitations)  
  
 Pour plus d'informations sur la mise en route avec ces types de projet, consultez les rubriques suivantes :  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Solutions Word](../vsto/word-solutions.md)  
  
-   [Solutions Excel](../vsto/excel-solutions.md)  
  
-   [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [Procédure pas à pas : création de votre première personnalisation au niveau du document pour Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a> Compléments VSTO  
 Le nœud **Office/SharePoint** dans la boîte de dialogue **Nouveau projet** fournit les modèles de projets suivants pour vous aider à créer des compléments VSTO.  
  
-   **Complément VSTO pour Excel 2013 et 2016**  
  
-   **Complément VSTO pour InfoPath 2013**  
  
-   **Complément VSTO pour Outlook 2013 et 2016**  
  
-   **Complément VSTO pour PowerPoint 2013 et 2016**  
  
-   **Complément pour Project 2013 et 2016**  
  
-   **Complément pour Visio 2013 et 2016**  
  
-   **Complément pour Word 2013 et 2016**  
  
-   **Complément pour Excel 2010**  
  
-   **Complément pour InfoPath 2010**  
  
-   **Complément pour Outlook 2010**  
  
-   **Complément pour PowerPoint 2010**  
  
-   **Complément pour Project 2010**  
  
-   **Complément pour Visio 2010**  
  
-   **Complément pour Word 2010**  
  
 Lorsque vous créez un projet basé sur l'un de ces modèles de projet, le code de votre solution s'exécute lorsque l'application associée est ouverte. Contrairement aux projets au niveau du document, le code n'est pas associé à un document unique.  
  
 Pour plus d'informations sur la mise en route avec ces types de projet, consultez les rubriques suivantes :  
  
-   [Bien démarrer avec la programmation des compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Procédure pas à pas : création de votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>Solutions basées sur un document ou sur un modèle  
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
  
##  <a name="Limitations"></a> Limitations des modèles globaux et des compléments Excel (fichiers .xla)  
 Les documents, classeurs et modèles peuvent ne pas fonctionner correctement en tant que modèles globaux ou compléments VSTO Excel (fichiers .xla).  
  
## <a name="word-templates"></a>Modèles Word  
 Si un modèle Microsoft Office Word a des extensions de code managé, l'assembly de projet n'est pas appelé si le modèle est attaché en tant que modèle global ou chargé à partir du répertoire de démarrage de Word. En outre, le document ne reconnaît pas le format d'un modèle faisant partie d'une solution Office.  
  
## <a name="excel-add-ins-xla-files"></a>Compléments Excel (fichiers .xla)  
 Il n’existe aucun projet Office permettant de créer un complément VSTO Excel (fichier .xla). Il est possible d'enregistrer un classeur en tant que fichier .xla, mais cette opération, qui n'est pas prise en charge, n'est pas recommandée. Si vous enregistrez un classeur qui a des extensions de code managé une **complément Microsoft Office Excel (\*.xla)** fichier, vous pouvez le sélectionner dans le **compléments** boîte de dialogue à appliquer à un autre classeur. Parfois, le code s’exécute dans le classeur cible après l’application du complément VSTO, mais une telle utilisation de la solution Office n’est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Développement de Solutions Office](../vsto/developing-office-solutions.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Prise en main de programmation des personnalisations au niveau du Document pour Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Prise en main de programmation des personnalisations au niveau du Document pour Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Bien démarrer avec la programmation des compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  