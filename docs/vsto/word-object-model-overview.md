---
title: "Vue d&#39;ensemble du mod&#232;le objet Word | Microsoft Docs"
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
  - "modèle objet Word"
  - "Word (développement Office dans Visual Studio), modèle objet"
  - "modèles objet (développement Office dans Visual Studio), Office"
  - "modèles objet (développement Office dans Visual Studio), Word"
  - "objets (développement Office dans Visual Studio), modèles objet Office"
  - "modèles objet Office"
ms.assetid: b66a7d9e-0a51-4ef5-8754-b2b899f9094c
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 77
---
# Vue d&#39;ensemble du mod&#232;le objet Word
  Quand vous développez des solutions Word dans Visual Studio, vous interagissez avec le modèle objet Word. Ce modèle objet se compose de classes et d'interfaces fournies dans l'assembly PIA \(Primary Interop Assembly\) pour Word et définies dans l'espace de noms <xref:Microsoft.Office.Interop.Word>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Cette rubrique propose une brève présentation du modèle objet Word. Pour obtenir la liste des ressources fournissant des informations complémentaires sur le modèle objet Word complet, consultez [Utilisation de la documentation du modèle objet Word](#WordOMDocumentation).  
  
 Pour obtenir des informations sur l'utilisation du modèle objet Word pour effectuer des tâches spécifiques, consultez les rubriques suivantes :  
  
-   [Utilisation de documents](../vsto/working-with-documents.md)  
  
-   [Utilisation de texte dans des documents](../vsto/working-with-text-in-documents.md)  
  
-   [Utilisation de tableaux](../vsto/working-with-tables.md)  
  
##  <a name="understanding"></a> Présentation du modèle objet Word  
 Word fournit des centaines d'objets avec lesquels vous pouvez interagir. Ces objets sont organisés selon une hiérarchie qui suit étroitement l'interface utilisateur. L'objet <xref:Microsoft.Office.Interop.Word.Application> se trouve en haut de la hiérarchie. Cet objet représente l'instance active de Word. L'objet <xref:Microsoft.Office.Interop.Word.Application> contient les objets <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark> et <xref:Microsoft.Office.Interop.Word.Range>. Chacun de ces objets possède de nombreuses méthodes et propriétés auxquelles vous pouvez accéder pour manipuler l'objet et interagir avec lui.  
  
 L'illustration suivante montre une vue de ces objets dans la hiérarchie du modèle objet Word.  
  
 ![Graphique du modèle objet Word](../vsto/media/wrwordobjectmodel.gif "Graphique du modèle objet Word")  
  
 À première vue, les objets semblent se chevaucher. Par exemple, les objets <xref:Microsoft.Office.Interop.Word.Document> et <xref:Microsoft.Office.Interop.Word.Selection> sont tous deux membres de l'objet <xref:Microsoft.Office.Interop.Word.Application>, mais l'objet <xref:Microsoft.Office.Interop.Word.Document> est également membre de l'objet <xref:Microsoft.Office.Interop.Word.Selection>. Les objets <xref:Microsoft.Office.Interop.Word.Document> et <xref:Microsoft.Office.Interop.Word.Selection> contiennent tous les deux les objets <xref:Microsoft.Office.Interop.Word.Bookmark> et <xref:Microsoft.Office.Interop.Word.Range>. Ce chevauchement existe parce qu'il existe plusieurs manières d'accéder au même type d'objet. Vous pouvez par exemple appliquer une mise en forme à un objet <xref:Microsoft.Office.Interop.Word.Range>, mais souhaiter accéder à la plage de la sélection actuelle, d'un paragraphe particulier, d'une section ou du document entier.  
  
 Les sections suivantes décrivent brièvement les objets de niveau supérieur et la façon dont ils interagissent les uns avec les autres. Ces objets incluent les cinq éléments suivants :  
  
-   Objet Application  
  
-   Objet Document  
  
-   Objet Selection  
  
-   Range \(objet\)  
  
-   Objet Bookmark  
  
 Outre le modèle objet Word, les projets Office dans Visual Studio fournissent des *éléments hôtes* et des *contrôles hôtes* qui étendent certains objets du modèle objet Word. Les éléments hôtes et les contrôles hôtes se comportent comme les objets Word qu'ils étendent, mais ils possèdent également des fonctionnalités supplémentaires, telles que la liaison de données, et des événements supplémentaires. Pour plus d’informations, consultez [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md) et [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
### Objet Application  
 L'objet <xref:Microsoft.Office.Interop.Word.Application> représente l'application Word et est le parent de tous les autres objets. Ses membres s'appliquent généralement à Word dans son ensemble. Vous pouvez utiliser ses propriétés et méthodes pour contrôler l'environnement Word.  
  
 Dans les projets de compléments VSTO, vous pouvez accéder à l'objet <xref:Microsoft.Office.Interop.Word.Application> à l'aide du champ `Application` de la classe `ThisAddIn`. Pour plus d'informations, consultez [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Dans les projets au niveau du document, vous pouvez accéder à l'objet <xref:Microsoft.Office.Interop.Word.Application> en utilisant la propriété <xref:Microsoft.Office.Tools.Word.Document.Application%2A> de la classe `ThisDocument`.  
  
### Objet Document  
 L'objet <xref:Microsoft.Office.Interop.Word.Document> est essentiel à la programmation de Word. Il représente un document et tout son contenu. Quand vous ouvrez ou créez un document, vous créez un objet <xref:Microsoft.Office.Interop.Word.Document>, qui est ajouté à la collection <xref:Microsoft.Office.Interop.Word.Documents> de l'objet <xref:Microsoft.Office.Interop.Word.Application>. Le document qui a le focus est appelé document actif. Il est représenté par la propriété <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> de l'objet <xref:Microsoft.Office.Interop.Word.Application>.  
  
 Les outils de développement Office dans Visual Studio étendent l'objet <xref:Microsoft.Office.Interop.Word.Document> en fournissant le type <xref:Microsoft.Office.Tools.Word.Document>. Ce type est un *élément hôte* qui vous donne accès à toutes les fonctionnalités d'un objet <xref:Microsoft.Office.Interop.Word.Document> et ajoute des événements supplémentaires et la possibilité d'ajouter des contrôles managés.  
  
 Quand vous créez un projet au niveau du document, vous pouvez accéder aux membres <xref:Microsoft.Office.Tools.Word.Document> en utilisant la classe `ThisDocument` générée dans votre projet. Vous pouvez accéder aux membres de l'élément hôte <xref:Microsoft.Office.Tools.Word.Document> en utilisant les mots clés **Me** ou **this** à partir du code dans la classe `ThisDocument` ou en utilisant `Globals.ThisDocument` à partir du code situé en dehors de la classe `ThisDocument`. Pour plus d'informations, consultez [Programmation de personnalisations au niveau du document](../vsto/programming-document-level-customizations.md). Par exemple, pour sélectionner le premier paragraphe du document, utilisez le code suivant :  
  
 [!code-csharp[Trin_VstcoreWordAutomation#120](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#120)]
 [!code-vb[Trin_VstcoreWordAutomation#120](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#120)]  
  
 Dans les projets de compléments VSTO, vous pouvez générer des éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> au moment de l'exécution. Vous pouvez utiliser l'élément hôte généré pour ajouter des contrôles au document associé. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### Objet Selection  
 L'objet <xref:Microsoft.Office.Interop.Word.Selection> représente la zone actuellement sélectionnée. Quand vous effectuez une opération dans l'interface utilisateur de Word, comme mettre du texte en gras, vous sélectionnez ou mettez en surbrillance le texte puis appliquez la mise en forme. L'objet <xref:Microsoft.Office.Interop.Word.Selection> est toujours présent dans un document. Si rien n'est sélectionné, il représente le point d'insertion. En outre, une sélection peut comprendre plusieurs blocs de texte non contigus.  
  
### Objet Range  
 L'objet <xref:Microsoft.Office.Interop.Word.Range> représente une zone contiguë dans un document et il est défini par une position de caractère de début et une position de caractère de fin. Vous n'êtes pas limité à un seul objet <xref:Microsoft.Office.Interop.Word.Range>. Vous pouvez définir plusieurs objets <xref:Microsoft.Office.Interop.Word.Range> dans un même document. Un objet <xref:Microsoft.Office.Interop.Word.Range> a les caractéristiques suivantes :  
  
-   Il peut être constitué du point d'insertion seul, d'une plage de texte ou de l'intégralité du document.  
  
-   Il inclut des caractères non imprimables tels que des espaces, des tabulations et des marques de paragraphe.  
  
-   Il peut correspondre à la zone représentée par la sélection actuelle ou il peut représenter une zone différente de la sélection actuelle.  
  
-   Il n'est pas visible dans un document, contrairement à une sélection, qui est toujours visible.  
  
-   Il n'est pas enregistré avec un document et il existe uniquement pendant l'exécution du code.  
  
 Quand vous insérez du texte à la fin d'une plage, Word étend automatiquement la plage pour inclure le texte inséré.  
  
### Objets de contrôle de contenu  
 Un objet <xref:Microsoft.Office.Interop.Word.ContentControl> vous permet de contrôler l'entrée et la présentation de texte et d'autres types de contenu dans les documents Word. Un objet <xref:Microsoft.Office.Interop.Word.ContentControl> peut afficher différents types d'interface utilisateur optimisés pour être utilisés dans des documents Word, comme un contrôle de texte enrichi, un sélecteur de date ou une zone de liste modifiable. Vous pouvez également utiliser <xref:Microsoft.Office.Interop.Word.ContentControl> pour empêcher les utilisateurs de modifier des sections du document ou du modèle.  
  
 Visual Studio étend l'objet <xref:Microsoft.Office.Interop.Word.ContentControl> en plusieurs contrôles hôtes différents. Alors que l'objet <xref:Microsoft.Office.Interop.Word.ContentControl> peut afficher tous les types d'interface utilisateur disponibles pour les contrôles de contenu, Visual Studio fournit un type différent pour chaque contrôle de contenu. Par exemple, vous pouvez utiliser un objet <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pour créer un contrôle de texte enrichi ou un objet <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> pour créer un sélecteur de date. Ces contrôles hôtes se comportent comme l'objet <xref:Microsoft.Office.Interop.Word.ContentControl> natif, mais ils possèdent des fonctionnalités de liaison de données et des événements supplémentaires. Pour plus d'informations, consultez [Contrôles de contenu](../vsto/content-controls.md).  
  
### Objet Bookmark  
 L'objet <xref:Microsoft.Office.Interop.Word.Bookmark> représente une zone contiguë dans un document, avec une position de début et une position de fin. Vous pouvez utiliser des signets pour marquer un emplacement dans un document ou comme conteneur de texte dans un document. Un objet <xref:Microsoft.Office.Interop.Word.Bookmark> peut être constitué du point d'insertion ou s'étendre à l'intégralité du document. Un objet <xref:Microsoft.Office.Interop.Word.Bookmark> présente les caractéristiques suivantes, qui le différencient de l'objet <xref:Microsoft.Office.Interop.Word.Range> :  
  
-   Vous pouvez nommer le signet au moment du design.  
  
-   Les objets <xref:Microsoft.Office.Interop.Word.Bookmark> sont enregistrés avec le document et ne sont donc pas supprimés à la fin de l'exécution du code ou à la fermeture du document.  
  
-   Vous pouvez masquer ou afficher les signets en attribuant à la propriété <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> de l'objet <xref:Microsoft.Office.Interop.Word.View> la valeur **false** ou la valeur **true**.  
  
 Visual Studio étend l'objet <xref:Microsoft.Office.Interop.Word.Bookmark> en fournissant le contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark>. Le contrôle hôte <xref:Microsoft.Office.Tools.Word.Bookmark> se comporte comme un objet <xref:Microsoft.Office.Interop.Word.Bookmark> natif, mais il possède des fonctionnalités de liaison de données et des événements supplémentaires. Vous pouvez lier des données à un contrôle de signet dans un document de la même façon que vous liez des données à un contrôle de zone de texte dans un Windows Form. Pour plus d'informations, consultez [Bookmark, contrôle](../vsto/bookmark-control.md).  
  
##  <a name="WordOMDocumentation"></a> Utilisation de la documentation du modèle objet Word  
 Pour obtenir des informations complètes sur le modèle objet Word, vous pouvez vous reporter à la documentation de référence de l'assembly PIA \(Primary Interop Assembly\) Word et à la documentation de référence du modèle objet VBA \(Visual Basic pour Applications\).  
  
### Documentation de référence de l'assembly PIA \(Primary Interop Assembly\)  
 La documentation de référence de l'assembly PIA Word décrit les types figurant dans l'assembly PIA pour Word. Cette documentation est disponible à l’emplacement suivant : [Documentation de référence de l’assembly PIA \(Primary Interop Assembly\) Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Pour plus d’informations sur la conception de l’assembly PIA Word, telles que les différences entre les classes et les interfaces dans l’assembly PIA, et l’implémentation des événements dans l’assembly PIA, consultez [Vue d’ensemble des classes et des interfaces dans les assemblys PIA \(Primary Interop Assembly\) Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### Documentation de référence du modèle objet VBA  
 La documentation de référence du modèle objet VBA présente le modèle objet Word tel qu'il est exposé au code VBA. Pour plus d’informations, consultez [Référence du modèle objet Word 2010](http://go.microsoft.com/fwlink/?LinkId=199772).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Word. Par exemple, l'objet Document mentionné dans la documentation de référence du modèle objet VBA correspond à l'objet <xref:Microsoft.Office.Interop.Word.Document> dans l'assembly PIA Word. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans cette documentation de référence en code Visual Basic ou Visual C\# pour pouvoir les utiliser dans un projet Word créé à l'aide de Visual Studio.  
  
## Voir aussi  
 [Assemblys PIA &#40;Primary Interop Assembly&#41; Office](../vsto/office-primary-interop-assemblies.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Utilisation de documents](../vsto/working-with-documents.md)   
 [Utilisation de texte dans des documents](../vsto/working-with-text-in-documents.md)   
 [Utilisation de tableaux](../vsto/working-with-tables.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  