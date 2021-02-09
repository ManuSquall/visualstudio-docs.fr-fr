---
title: solutions Word
description: Découvrez comment vous pouvez utiliser les solutions Visual Studio pour automatiser Word, étendre les fonctionnalités de Word et personnaliser l’interface utilisateur de Word.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 91f262fb88d95be586869b22559e171f4a01ed16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847633"
---
# <a name="word-solutions"></a>solutions Word
  Visual Studio fournit des modèles de projet que vous pouvez utiliser pour créer des personnalisations au niveau du document et des compléments VSTO pour Microsoft Office Word. Vous pouvez utiliser ces solutions pour automatiser Word, étendre des fonctionnalités Word et personnaliser l'interface utilisateur de Word. Pour plus d’informations sur les différences entre les personnalisations au niveau du document et les compléments VSTO, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Cette rubrique fournit les informations suivantes :

- [Automatiser Word](#automating).

- [Développez des personnalisations au niveau du document pour Word](#doclevel).

- [Développez des compléments VSTO pour Word](#applevel).

- [Personnaliser l’interface utilisateur de Word](#UI).

## <a name="automate-word"></a><a name="automating"></a> Automatiser Word
 Le modèle objet Word expose de nombreux types que vous pouvez utiliser pour automatiser Word. Par exemple, vous pouvez, par programmation, créer des tableaux, mettre en forme des documents, ainsi que définir le texte dans des plages et des paragraphes. Pour plus d’informations, consultez [vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md).

 Lorsque vous développez des solutions Word dans Visual Studio, vous pouvez également utiliser des *éléments hôtes* et des *contrôles hôtes* dans vos solutions. Il s'agit d'objets qui étendent certains objets couramment utilisés dans le modèle objet Word, tels que les objets <xref:Microsoft.Office.Interop.Word.Document> et <xref:Microsoft.Office.Interop.Word.ContentControl> . Les objets étendus se comportent comme les objets Word sur lesquels ils sont basés, mais ils ajoutent des événements supplémentaires et des fonctionnalités de liaison de données aux objets. Pour plus d’informations, consultez [automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-word"></a><a name="doclevel"></a> Développer des personnalisations au niveau du document pour Word
 Une personnalisation au niveau du document pour Microsoft Office Word se compose d'un assembly qui est associé à un document spécifique. L'assembly augmente généralement les fonctionnalités du document en personnalisant l'interface utilisateur et en automatisant Word. Contrairement à un complément VSTO, qui est associé à Word lui-même, les fonctionnalités que vous implémentez dans une personnalisation sont disponibles uniquement lorsque le document associé est ouvert dans Word.

 Pour créer un projet de personnalisation au niveau du document pour Word, utilisez les modèles de projet de document Word ou de modèle Word dans la boîte de dialogue **Nouveau projet** de Visual Studio. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Pour plus d’informations sur le fonctionnement des personnalisations au niveau [du document, architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Modèle de programmation de personnalisation Word
 Lorsque vous créez un projet au niveau du document pour Word, Visual Studio génère une classe, appelée `ThisDocument`, qui constitue la base de votre solution. Cette classe représente le document associé à votre solution, et fournit les informations de base nécessaires à l'écriture de votre code.

 Pour plus d’informations sur la `ThisDocument` classe et les autres fonctionnalités que vous pouvez utiliser dans un projet au niveau du document, consultez [programmes de personnalisation au niveau du document](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-word"></a><a name="applevel"></a> Développer des compléments VSTO pour Word
 Un complément VSTO pour Microsoft Office Word se compose d'un assembly qui est chargé par Word. L'assembly étend généralement les fonctionnalités Word en personnalisant l'interface utilisateur et en automatisant Word. Contrairement à une personnalisation au niveau du document, qui est associée à un document spécifique, les fonctionnalités que vous implémentez dans un complément VSTO ne sont pas limitées à un seul document.

 Pour créer un projet de complément VSTO pour Word, utilisez les modèles de projet de complément Word proposés dans la boîte de dialogue **Nouveau projet** de Visual Studio. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Pour obtenir des informations générales sur le fonctionnement des compléments VSTO, consultez [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Modèle de programmation de complément Word
 Quand vous créez un projet de complément VSTO Word, Visual Studio génère une classe, appelée `ThisAddIn`, qui constitue la base de votre solution. Cette classe fournit les informations de base nécessaires à l’écriture de votre code, et elle expose également le modèle objet de Word à votre complément VSTO.

 Pour plus d’informations sur la `ThisAddIn` classe et les autres fonctionnalités que vous pouvez utiliser dans un complément VSTO, consultez [compléments VSTO du programme](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-word"></a><a name="UI"></a> Personnaliser l’interface utilisateur de Word
 Il existe différentes façons de personnaliser l'interface utilisateur de Word. Certaines options sont disponibles pour tous les types de projets, tandis que d'autres options sont disponibles uniquement pour les compléments VSTO ou les personnalisations au niveau du document.

### <a name="options-for-all-project-types"></a>Options pour tous les types de projets
 Le tableau suivant répertorie les options de personnalisation qui sont disponibles pour les personnalisations au niveau du document et les compléments VSTO.

|Tâche|Informations supplémentaires|
|----------|--------------------------|
|Personnaliser le ruban.|[Vue d’ensemble du ruban](../vsto/ribbon-overview.md)|
|Ajouter des contrôles Windows Forms ou des contrôles Word étendus au document personnalisé (pour une personnalisation au niveau du document) ou à tout document ouvert (pour un complément VSTO).|[Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Comment : ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Comment : ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Options pour les personnalisations au niveau du document
 Le tableau suivant répertorie les options de personnalisation qui sont disponibles uniquement pour les personnalisations au niveau du document.

|Tâche|Informations supplémentaires|
|----------|--------------------------|
|Ajouter un volet Actions au document.|[Vue d’ensemble du volet Actions](../vsto/actions-pane-overview.md)<br /><br /> [Comment : ajouter un volet actions à des documents Word ou à des classeurs Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Ajouter des contrôles étendus XMLNode et XMLNodes à la surface du document.|[Comment : ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Comment : ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Options pour les compléments VSTO
 Le tableau suivant répertorie les options de personnalisation qui sont disponibles uniquement pour les compléments VSTO.

|Tâche|Informations supplémentaires|
|----------|--------------------------|
|Créer un volet des tâches personnalisé.|[Volets des tâches personnalisés](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble du modèle objet Word](../vsto/word-object-model-overview.md)|Fournit une vue d'ensemble des principaux types fournis par le modèle objet Word.|
|[Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)|Fournit des informations sur les objets étendus (fournis par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que vous pouvez utiliser dans les solutions Word.|
|[Vue d’ensemble des contrôles de Windows Forms sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Explique comment ajouter des contrôles Windows Forms à des documents Word.|
|[Procédure pas à pas : création de votre première personnalisation au niveau du document pour Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Montre comment créer une personnalisation de base au niveau du document pour Word.|
|[Procédure pas à pas : créer votre premier complément VSTO pour Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Montre comment créer un complément VSTO de base pour Word.|
|[Procédure pas à pas : ajout de contrôles à un document au moment de l’exécution dans un complément VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Montre comment ajouter un bouton Windows Forms et un contrôle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> à un document au moment de l'exécution à l'aide d'un complément VSTO.|
|[Word 2010 dans le développement Office](/previous-versions/office/developer/office-2010/ff601860(v=office.14))|Fournit des liens vers des articles et de la documentation de référence sur le développement de solutions Word (non spécifiques au développement Office avec Visual Studio).|
