---
title: Vue d’ensemble de parties XML personnalisée
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b0cc9e30cbc55164e8ee993930c6d5fca639a318
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942441"
---
# <a name="custom-xml-parts-overview"></a>Vue d’ensemble de parties XML personnalisée
  Vous pouvez incorporer des données XML dans des documents pour certaines applications Microsoft Office. Lorsque vous incorporez des données XML dans un document, elles sont appelées une *partie XML personnalisée*.  
  
 Vous pouvez créer et modifier des parties XML personnalisées dans un document en utilisant un complément VSTO ou une solution au niveau du document dans Visual Studio. Vous n'avez pas besoin de démarrer l'application Microsoft Office pour créer et modifier des parties XML personnalisées.  
  
 **S’applique à :** Les informations contenues dans cette rubrique s’applique aux projets de niveau document et de complément VSTO pour Excel, PowerPoint et Word. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio permet également de mettre en cache des objets de données dans des personnalisations au niveau du document. Cette fonctionnalité diffère des parties XML personnalisées, malgré certaines ressemblances. Pour plus d’informations, consultez [mis en cache des données dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Comprendre les parties XML personnalisées  
 Les parties XML personnalisées ont été introduites dans la version 2007 de Microsoft Office System, tout comme les formats Open XML. Ces formats incluent de nouveaux formats de fichier basé sur XML pour Excel, PowerPoint et Word (tels que *.xlsx*, *.pptx*, et *.docx*). Documents dans ces formats se composent de fichiers XML (également nommé *des parties XML*) qui sont organisés en dossiers dans une archive ZIP. La plupart des parties XML sont intégrées et facilitent la définition de la structure et de l'état du document. Toutefois, les documents peuvent également contenir des parties XML personnalisées, que vous pouvez utiliser pour stocker des données XML arbitraires dans les documents.  
  
 Met en forme le fichier XML permettent aux applications de travailler avec des documents qui ne sont pas possibles avec les anciens formats de fichier binaire (tel que *.xls*, *.ppt*, et *.doc*). Toute application qui peut lire des archives ZIP peut examiner et modifier le contenu des documents, même si Microsoft Office n'est pas installé.  
  
 Pour plus d'informations sur la structure d'Open XML et des parties XML personnalisées, consultez les articles suivants :  
  
-   [Présentation des formats de fichier Open XML Office (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
-   [Guide pratique pour Manipuler des documents aux formats Open XML](/previous-versions/office/developer/office-2007/aa982683(v=office.12))  
  
-   [Procédure pas à pas : Format Word 2007 XML](/previous-versions/office/developer/office-2007/bb266220(v=office.12))  
  
-   [Créer des documents Word 2007 à l’aide des formats Open XML](/previous-versions/office/developer/office-2007/bb264572(v=office.12))  
  
> [!NOTE]  
>  Excel, Word et PowerPoint vous permettent également d'utiliser les parties XML personnalisées dans des documents enregistrés dans les formats de fichier binaires. Toutefois, si un document est enregistré dans un format binaire, vous ne pouvez pas ajouter ni modifier de parties XML personnalisées sans démarrer l'application Microsoft Office.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Créer et modifier des parties XML personnalisées  
 Vous pouvez créer ou modifier des parties XML personnalisées quand le document est ouvert dans l'application Office ou quand le document est fermé, même si Microsoft Office n'est pas installé.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modifier des parties XML pendant l’exécution de l’application Office  
 Vous pouvez travailler avec des parties XML personnalisées à l’aide d’une personnalisation au niveau du document ou un composant logiciel complément VSTO. Dans le cas d'une personnalisation au niveau du document, vous utilisez généralement les parties XML personnalisées qui figurent dans le document personnalisé. Si vous utilisez un composant logiciel complément VSTO, vous pouvez créer ou modifier des parties XML personnalisées dans n’importe quel document est ouvert dans l’application.  
  
 Pour créer une partie XML personnalisée au moyen de Visual Studio, ajoutez un nouveau <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> dans le document. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Guide pratique pour Ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Guide pratique pour Ajouter des parties XML personnalisées à des documents à l’aide des Compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modifier des parties XML sans démarrer l’application Office  
 Vous pouvez ajouter ou modifier une partie XML personnalisée sans démarrer Excel, PowerPoint ni Word. Cela est utile si vous souhaitez utiliser les données XML d'un document sur un ordinateur qui ne dispose pas des applications Microsoft Office, tel qu'un serveur.  
  
 Pour ajouter une partie XML personnalisée sans démarrer Microsoft Office, utilisez les classes du Kit de développement logiciel (SDK) Open XML. Ces classes ont été conçues pour fournir l'accès au contenu Open XML spécifique aux documents Office. Par exemple, pour ajouter une partie XML personnalisée à un classeur Excel, vous utilisez le <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> méthode d’un <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> objet. Pour plus d’informations, consultez [SDK Open XML](/office/open-xml/open-xml-sdk).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Lier des parties XML personnalisées aux contrôles de contenu Word  
 Vous pouvez lier des contrôles de contenu d'une solution Word à des éléments figurant dans une partie XML personnalisée. Quand un contrôle de contenu est lié à une partie XML personnalisée, les données figurant dans la partie XML personnalisée s'affichent dans l'interface utilisateur du contrôle de contenu. Si un utilisateur modifie le texte du contrôle, l'élément XML correspondant est automatiquement mis à jour. De la même façon, si les valeurs des éléments figurant dans les parties XML personnalisées sont modifiées, les contrôles de contenu liés aux éléments XML affichent les nouvelles données. Pour plus d’informations, consultez [contrôles de contenu](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas XML et des données dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Guide pratique pour Ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Guide pratique pour Ajouter des parties XML personnalisées à des documents à l’aide des Compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Procédure pas à pas : Lier des contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
