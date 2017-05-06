---
title: "Vue d&#39;ensemble des parties XML personnalis&#233;es"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "parties XML personnalisées (développement Office dans Visual Studio)"
  - "parties XML personnalisées (développement Office dans Visual Studio), à propos de"
  - "données (développement Office dans Visual Studio), parties XML personnalisées"
  - "documents (développement Office dans Visual Studio), parties XML personnalisées"
  - "incorporer des données XML dans des documents (développement Office dans Visual Studio)"
  - "Excel (développement Office dans Visual Studio), parties XML personnalisées"
  - "documents Office (développement Office dans Visual Studio), parties XML personnalisées"
  - "formats Office Open XML (développement Office dans Visual Studio)"
  - "Word (développement Office dans Visual Studio), parties XML personnalisées"
  - "XML (développement Office dans Visual Studio), parties XML personnalisées"
  - "formats de fichier XML (développement Office dans Visual Studio)"
  - "parties XML (développement Office dans Visual Studio)"
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Vue d&#39;ensemble des parties XML personnalis&#233;es
  Vous pouvez incorporer des données XML dans des documents pour certaines applications Microsoft Office.  Quand des données XML sont incorporées dans un document, elles sont appelées *partie XML personnalisée*.  
  
 Vous pouvez créer et modifier des parties XML personnalisées dans un document en utilisant un complément VSTO ou une solution au niveau du document dans Visual Studio.  Vous n'avez pas besoin de démarrer l'application Microsoft Office pour créer et modifier des parties XML personnalisées.  
  
 **S'applique à :** les informations de cette rubrique s'appliquent aux projets de niveau document et aux projets de compléments VSTO pour Excel, PowerPoint et Word.  Pour plus d'informations, consultez [Fonctionnalités disponibles par type d'application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio permet également de mettre en cache des objets de données dans des personnalisations au niveau du document.  Cette fonctionnalité diffère des parties XML personnalisées, malgré certaines ressemblances.  Pour plus d'informations, consultez [Données mises en cache dans des personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md).  
  
## Présentation des parties XML personnalisées  
 Les parties XML personnalisées ont été introduites dans la version 2007 de Microsoft Office System, tout comme les formats Open XML.  Ces formats incluent de nouveaux formats de fichier XML pour Excel, PowerPoint et Word \(tels que .xlsx, .pptx et .docx\).  Les documents dans ces formats se composent de fichiers XML \(également appelés *parties XML*\) qui sont organisés en dossiers dans une archive ZIP.  La plupart des parties XML sont intégrées et facilitent la définition de la structure et de l'état du document.  Toutefois, les documents peuvent également contenir des parties XML personnalisées, que vous pouvez utiliser pour stocker des données XML arbitraires dans les documents.  
  
 Les formats de fichier XML permettent aux applications d'utiliser les documents selon des manières que ne permettent pas les anciens formats de fichier binaires \(tels que .xls, .ppt et .doc\).  Toute application qui peut lire des archives ZIP peut examiner et modifier le contenu des documents, même si Microsoft Office n'est pas installé.  
  
 Pour plus d'informations sur la structure d'Open XML et des parties XML personnalisées, consultez les articles suivants :  
  
-   [Présentation des formats de fichier Open XML Microsoft Office \(2007\)](http://msdn.microsoft.com/fr-fr/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Comment : manipuler les documents aux formats Open XML](http://msdn.microsoft.com/fr-fr/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Procédure pas à pas : format XML Word 2007](http://msdn.microsoft.com/fr-fr/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Création de documents Word 2007 à l'aide des formats Open XML](http://msdn.microsoft.com/fr-fr/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word et PowerPoint vous permettent également d'utiliser les parties XML personnalisées dans des documents enregistrés dans les formats de fichier binaires.  Toutefois, si un document est enregistré dans un format binaire, vous ne pouvez pas ajouter ni modifier de parties XML personnalisées sans démarrer l'application Microsoft Office.  
  
## Création et modification de parties XML personnalisées  
 Vous pouvez créer ou modifier des parties XML personnalisées quand le document est ouvert dans l'application Office ou quand le document est fermé, même si Microsoft Office n'est pas installé.  
  
### Modification des parties XML quand l'application Office est en cours d'exécution  
 Vous pouvez utiliser des parties XML personnalisées au moyen d'une personnalisation au niveau du document ou à l'aide d'un complément VSTO.  Dans le cas d'une personnalisation au niveau du document, vous utilisez généralement les parties XML personnalisées qui figurent dans le document personnalisé.  Si vous utilisez un complément VSTO, vous pouvez créer ou modifier des parties XML personnalisées dans n'importe quel document ouvert dans l'application.  
  
 Pour créer une partie XML personnalisée au moyen de Visual Studio, ajoutez un nouveau <xref:Microsoft.Office.Core.CustomXMLPart> à la collection <xref:Microsoft.Office.Core.CustomXMLParts> dans le document.  Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Comment : ajouter des parties XML personnalisées à des documents à l'aide de compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### Modification des parties XML sans démarrer l'application Office  
 Vous pouvez ajouter ou modifier une partie XML personnalisée sans démarrer Excel, PowerPoint ni Word.  Cela est utile si vous souhaitez utiliser les données XML d'un document sur un ordinateur qui ne dispose pas des applications Microsoft Office, tel qu'un serveur.  
  
 Pour ajouter une partie XML personnalisée sans démarrer Microsoft Office, utilisez les classes du Kit de développement logiciel \(SDK\) Open XML.  Ces classes ont été conçues pour fournir l'accès au contenu Open XML spécifique aux documents Office.  Par exemple, pour ajouter une partie XML personnalisée à un classeur Excel, vous utilisez la méthode [AddNewPart\<T\>](http://msdn.microsoft.com/fr-fr/47c348c0-77ab-a504-5097-bcd6a213921a) d'un objet [WorkbookPart](http://msdn.microsoft.com/fr-fr/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2).  Pour plus d'informations, consultez [Kit de développement logiciel \(SDK\) Open XML 2.0](http://msdn.microsoft.com/fr-fr/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## Liaison de parties XML personnalisées à des contrôles de contenu Word  
 Vous pouvez lier des contrôles de contenu d'une solution Word à des éléments figurant dans une partie XML personnalisée.  Quand un contrôle de contenu est lié à une partie XML personnalisée, les données figurant dans la partie XML personnalisée s'affichent dans l'interface utilisateur du contrôle de contenu.  Si un utilisateur modifie le texte du contrôle, l'élément XML correspondant est automatiquement mis à jour.  De la même façon, si les valeurs des éléments figurant dans les parties XML personnalisées sont modifiées, les contrôles de contenu liés aux éléments XML affichent les nouvelles données.  Pour plus d'informations, consultez [Contrôles de contenu](../vsto/content-controls.md).  
  
## Voir aussi  
 [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Comment : ajouter des parties XML personnalisées aux personnalisations au niveau du document](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Comment : ajouter des parties XML personnalisées à des documents à l'aide de compléments VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Procédure pas à pas : liaison de contrôles de contenu à des parties XML personnalisées](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  