---
title: "Vue d’ensemble des parties XML personnalisées | Documents Microsoft"
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
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8dc3e4b1abc5f60f9ca63e374ab8870df6bb0d41
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="custom-xml-parts-overview"></a>Custom XML Parts Overview
  Vous pouvez incorporer des données XML dans des documents pour certaines applications Microsoft Office. Lorsque vous incorporez des données XML dans un document, les données se nomme un *partie XML personnalisée*.  
  
 Vous pouvez créer et modifier des parties XML personnalisées dans un document en utilisant un complément VSTO ou une solution au niveau du document dans Visual Studio. Vous n'avez pas besoin de démarrer l'application Microsoft Office pour créer et modifier des parties XML personnalisées.  
  
 **S’applique à :** les informations contenues dans cette rubrique s’applique aux projets de niveau document et les projets de complément VSTO pour Excel, PowerPoint et Word. Pour plus d'informations, consultez [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio permet également de mettre en cache des objets de données dans des personnalisations au niveau du document. Cette fonctionnalité diffère des parties XML personnalisées, malgré certaines ressemblances. Pour plus d’informations, consultez [mis en cache les données dans les personnalisations au niveau du Document](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understanding-custom-xml-parts"></a>Présentation des parties XML personnalisées  
 Les parties XML personnalisées ont été introduites dans la version 2007 de Microsoft Office System, tout comme les formats Open XML. Ces formats incluent de nouveaux formats de fichier XML pour Excel, PowerPoint et Word (tels que .xlsx, .pptx et .docx). Documents dans ces formats se composent de fichiers XML (également appelée *des parties XML*) qui sont organisés en dossiers dans une archive ZIP. La plupart des parties XML sont intégrées et facilitent la définition de la structure et de l'état du document. Toutefois, les documents peuvent également contenir des parties XML personnalisées, que vous pouvez utiliser pour stocker des données XML arbitraires dans les documents.  
  
 Les formats de fichier XML permettent aux applications d'utiliser les documents selon des manières que ne permettent pas les anciens formats de fichier binaires (tels que .xls, .ppt et .doc). Toute application qui peut lire des archives ZIP peut examiner et modifier le contenu des documents, même si Microsoft Office n'est pas installé.  
  
 Pour plus d'informations sur la structure d'Open XML et des parties XML personnalisées, consultez les articles suivants :  
  
-   [Présentation des formats de fichier Open XML Microsoft Office (2007)](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Comment : manipuler des Documents au format Open XML](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Procédure pas à pas : Format XML Word 2007](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Formats de création de Documents Word 2007 à l’aide du format Open XML](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word et PowerPoint vous permettent également d'utiliser les parties XML personnalisées dans des documents enregistrés dans les formats de fichier binaires. Toutefois, si un document est enregistré dans un format binaire, vous ne pouvez pas ajouter ni modifier de parties XML personnalisées sans démarrer l'application Microsoft Office.  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>Création et modification de parties XML personnalisées  
 Vous pouvez créer ou modifier des parties XML personnalisées quand le document est ouvert dans l'application Office ou quand le document est fermé, même si Microsoft Office n'est pas installé.  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>Modification des parties XML quand l'application Office est en cours d'exécution  
 Vous pouvez utiliser des parties XML personnalisées au moyen d'une personnalisation au niveau du document ou à l'aide d'un complément VSTO. Dans le cas d'une personnalisation au niveau du document, vous utilisez généralement les parties XML personnalisées qui figurent dans le document personnalisé. Si vous utilisez un complément VSTO, vous pouvez créer ou modifier des parties XML personnalisées dans n'importe quel document ouvert dans l'application.  
  
 Pour créer une partie XML personnalisée au moyen de Visual Studio, ajoutez un nouveau <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> dans le document. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Guide pratique pour ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Guide pratique pour ajouter des parties XML personnalisées à des documents à l’aide de compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>Modification des parties XML sans démarrer l'application Office  
 Vous pouvez ajouter ou modifier une partie XML personnalisée sans démarrer Excel, PowerPoint ni Word. Cela est utile si vous souhaitez utiliser les données XML d'un document sur un ordinateur qui ne dispose pas des applications Microsoft Office, tel qu'un serveur.  
  
 Pour ajouter une partie XML personnalisée sans démarrer Microsoft Office, utilisez les classes du Kit de développement logiciel (SDK) Open XML. Ces classes ont été conçues pour fournir l'accès au contenu Open XML spécifique aux documents Office. Par exemple, pour ajouter une partie XML personnalisée à un classeur Excel, vous utilisez la [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a) méthode d’un [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) objet. Pour plus d’informations, consultez [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>Liaison de parties XML personnalisées à des contrôles de contenu Word  
 Vous pouvez lier des contrôles de contenu d'une solution Word à des éléments figurant dans une partie XML personnalisée. Quand un contrôle de contenu est lié à une partie XML personnalisée, les données figurant dans la partie XML personnalisée s'affichent dans l'interface utilisateur du contrôle de contenu. Si un utilisateur modifie le texte du contrôle, l'élément XML correspondant est automatiquement mis à jour. De la même façon, si les valeurs des éléments figurant dans les parties XML personnalisées sont modifiées, les contrôles de contenu liés aux éléments XML affichent les nouvelles données. Pour plus d'informations, consultez [Content Controls](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas XML et les données dans les personnalisations au niveau du Document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du Document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Comment : ajouter des parties XML personnalisées à des Documents à l’aide de compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  