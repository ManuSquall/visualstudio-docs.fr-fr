---
title: Automatiser Word à l’aide d’objets étendus
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2babc4c22da5d27027f63dd0e0ca54577daa5535
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956309"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatiser Word à l’aide d’objets étendus
  Quand vous développez des solutions Word dans Visual Studio, vous pouvez également utiliser des *éléments hôtes* et des *contrôles hôtes*dans vos solutions. Il s’agit d’objets qui étendent certains objets couramment utilisés dans le modèle objet Word (autrement dit, le modèle objet exposé par l’assembly PIA (Primary Interop Assembly) pour Word), par exemple les objets <xref:Microsoft.Office.Interop.Word.Document> et <xref:Microsoft.Office.Interop.Word.ContentControl> . Les objets étendus se comportent comme les objets Word sur lesquels ils sont basés, mais ils ajoutent des événements supplémentaires et des fonctionnalités de liaison de données aux objets.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Les éléments hôtes et les contrôles hôtes sont disponibles dans les compléments VSTO et les personnalisations au niveau du document. Toutefois, le contexte dans lequel ils peuvent être utilisés est différent pour chaque type de solution. Pour plus d’informations, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Élément hôte de document  
 Les projets Word vous donnent accès à l’élément hôte <xref:Microsoft.Office.Tools.Word.Document> . L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> sert de conteneur pour d’autres contrôles, notamment les contrôles hôtes et les contrôles Windows Forms. En outre, il gère les informations relatives aux contrôles sur sa surface. L’élément hôte <xref:Microsoft.Office.Tools.Word.Document> fournit aussi la plupart des mêmes membres que la classe <xref:Microsoft.Office.Interop.Word.Document> , qui est la classe correspondante dans le modèle objet de Word.  
  
 Pour plus d’informations, consultez [élément hôte de Document](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>contrôles hôtes Word  
 Il existe plusieurs contrôles hôtes pour Word qui vous aident à créer, organiser et automatiser des documents. La plupart de leurs fonctionnalités concernent l’importation, la présentation et la protection des données. Ces contrôles hôtes fournissent des événements et des fonctionnalités de liaison de données dont ne disposent pas leurs équivalents dans le modèle objet Word natif.  
  
 Dans les projets au niveau du document, vous pouvez ajouter n’importe quel contrôle hôte à votre document au moment du design, ou vous pouvez ajouter des contrôles de contenu et de contrôles bookmark au moment de l’exécution. Dans les projets de complément VSTO, vous pouvez ajouter des contrôles de contenu et les contrôles bookmark à tout document ouvert au moment de l’exécution.  
  
 Pour plus d’informations sur les contrôles hôtes que vous pouvez utiliser dans les projets Word, consultez les rubriques suivantes :  
  
-   [Contrôles de contenu](../vsto/content-controls.md)  
  
-   [Bookmark (contrôle)](../vsto/bookmark-control.md)  
  
-   [XMLNode, contrôle](../vsto/xmlnode-control.md)  
  
-   [XMLNodes, contrôle](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Ajouter des contrôles de contenu à des documents Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Guide pratique pour Ajouter des contrôles Bookmark à des documents Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Guide pratique pour Ajouter des contrôles XMLNode à des documents Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Guide pratique pour Ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Guide pratique pour Redimensionner les contrôles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Procédure pas à pas : Créer un modèle à l’aide de contrôles de contenu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Procédure pas à pas : Lier des contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Procédure pas à pas : Créer des menus contextuels pour les signets](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Solutions Word](../vsto/word-solutions.md)   
 [Éléments hôtes et la vue d’ensemble des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
