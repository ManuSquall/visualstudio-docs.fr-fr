---
title: Élément hôte de document
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea85d0f0f9435795abf75973373e6f0ae7e3a949
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647350"
---
# <a name="document-host-item"></a>Élément hôte de document
  L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> est un type qui étend le type <xref:Microsoft.Office.Interop.Word.Document> à partir de l’assembly PIA (Primary Interop Assembly) de Word. L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> fournit les mêmes propriétés, méthodes et événements qu’un objet <xref:Microsoft.Office.Interop.Word.Document> , mais il expose également des événements supplémentaires et agit comme conteneur pour les contrôles hôtes et les contrôles Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Dans les projets au niveau du document se trouve un élément hôte <xref:Microsoft.Office.Tools.Word.Document> par défaut qui représente le document dans votre projet. Dans les projets de compléments VSTO, vous pouvez générer des éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> au moment de l'exécution.  
  
## <a name="understand-the-document-host-item-in-document-level-projects"></a>Comprendre l’élément hôte de document dans les projets au niveau du document  
 Pour accéder au document dans votre projet, utilisez la classe `ThisDocument` . Lorsque vous créez un projet au niveau du document, Visual Studio génère la classe `ThisDocument` pour servir de liaison entre Word et votre code de personnalisation. La classe `ThisDocument` vous permet d’accéder aux membres de l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> pour effectuer des tâches de base dans votre personnalisation, comme l’exécution de code à l’ouverture ou la fermeture du document. Vous pouvez aussi utiliser la classe pour ajouter des contrôles au document. En combinant plusieurs jeux de contrôles et en écrivant du code, vous pouvez lier les contrôles à des données, recueillir des informations auprès de l’utilisateur et répondre aux actions de l’utilisateur. Pour plus d’informations, consultez [programmer des personnalisations au niveau du document](../vsto/programming-document-level-customizations.md).  
  
 La classe `ThisDocument` fournit un emplacement dans lequel vous pouvez commencer à écrire du code dans votre projet. Étant donné que la classe fournit les mêmes propriétés, méthodes et événements que l’objet <xref:Microsoft.Office.Interop.Word.Document> dans l’assembly PIA pour Word, vous pouvez aussi utiliser `ThisDocument` pour accéder au modèle objet de Word. Pour plus d’informations, consultez [vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Limitations de l’élément hôte de document dans les projets au niveau du document  
 Un projet au niveau du document peut contenir un seul élément hôte <xref:Microsoft.Office.Tools.Word.Document> (autrement dit, la classe `ThisDocument` ). Vous ne pouvez pas ajouter de nouveaux <xref:Microsoft.Office.Tools.Word.Document> hôte à votre projet au moment du design, et vous ne pouvez pas créer de nouveaux <xref:Microsoft.Office.Tools.Word.Document> héberger les éléments lors de l’exécution à partir d’une personnalisation au niveau du document.  
  
 Si vous créez un nouveau document Word lors de l’exécution, il sera du type <xref:Microsoft.Office.Interop.Word.Document>. Comme il ne s’agit pas d’un élément hôte, elle ne peut pas contenir de contrôles hôtes ni de contrôles Windows Forms. Pour plus d’informations sur la création de documents au moment de l’exécution, consultez [Comment : Créer par programme des documents](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understand-document-host-items-in-application-level-projects"></a>Comprendre les éléments hôtes document dans les projets de niveau application  
 Dans les projets complément VSTO, vous pouvez générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document> au moment de l’exécution pour tout document ouvert dans Word. Vous pouvez utiliser l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> pour ajouter des contrôles au document associé ou pour gérer des événements qui ne sont pas disponibles sur des objets <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Pour générer un élément hôte <xref:Microsoft.Office.Tools.Word.Document>, utilisez la méthode `GetVstoObject`. Pour plus d’informations, consultez [documents Word d’étendre et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Automatiser Word à l’aide d’objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Vue d’ensemble du modèle d’objet Word](../vsto/word-object-model-overview.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  