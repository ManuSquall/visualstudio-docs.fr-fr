---
title: "Proc&#233;dure pas &#224; pas : Liaison d&#39;un Type de contenu &#224; une Extension de nom de fichier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), lier de nouveau - type de contenu pour l'extension de nom de fichier"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Proc&#233;dure pas &#224; pas : Liaison d&#39;un Type de contenu &#224; une Extension de nom de fichier
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez définir votre propre type de contenu et lier une extension de nom de fichier à l'aide des extensions de l'éditeur Managed Extensibility Framework \(MEF\). Dans certains cas, l'extension de nom de fichier a déjà été définie par un service de langage ; Toutefois, pour l'utiliser avec MEF vous toujours devez le lier à un type de contenu.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d'un projet MEF  
  
1.  Créez un projet VSIX c\#. \(Dans le **Nouveau projet** boîte de dialogue, sélectionnez **Visual C\# \/ extensibilité**, puis **projet VSIX**.\) Nommez la solution `ContentTypeTest`.  
  
2.  Dans le **source.extension.vsixmanifest** fichier, accédez à la **actifs** onglet et définissez le **Type** champ **Microsoft.VisualStudio.MefComponent**, le **Source** champ **un projet dans la solution actuelle**, et le **projet** champ pour le nom du projet.  
  
## Définition du Type de contenu  
  
1.  Ajoutez un fichier de classe et nommez\-le `FileAndContentTypes`.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Ajoutez le code suivant `using` directives.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Déclarez une classe statique qui contient les définitions.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Dans cette classe, exporter un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> nommé « masqué » et déclarer sa définition de base « texte ».  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## Liaison d'une Extension de nom de fichier à un Type de contenu  
  
-   Pour mapper ce type de contenu à une extension de nom de fichier, exporter un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> qui a l'extension « .hid » et le type de contenu « masqué ».  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## Ajout du Type de contenu à une exportation de l'éditeur  
  
1.  Créez une extension de l'éditeur. Par exemple, vous pouvez utiliser l'extension de glyphe de marge décrite dans [Procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Ajoutez la classe définie dans cette procédure.  
  
3.  Lorsque vous exportez la classe d'extension, ajoutez un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de type « masqué » à celui\-ci.  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)