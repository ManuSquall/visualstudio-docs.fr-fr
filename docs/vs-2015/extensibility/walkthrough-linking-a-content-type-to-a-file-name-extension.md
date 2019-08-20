---
title: 'Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201992"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir votre propre type de contenu et lier une extension de nom de fichier à l’aide des extensions Managed Extensibility Framework (MEF) de l’éditeur. Dans certains cas, l’extension de nom de fichier a déjà été définie par un service de langage ; Néanmoins, pour l’utiliser avec MEF vous toujours devez le lier à un type de contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1. Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `ContentTypeTest`.  
  
2. Dans le **source.extension.vsixmanifest** fichier, accédez à la **actifs** onglet et définissez le **Type** champ **Microsoft.VisualStudio.MefComponent**, le **Source** champ **un projet dans la solution actuelle**et le **projet** champ pour le nom du projet.  
  
## <a name="defining-the-content-type"></a>La définition du Type de contenu  
  
1. Ajoutez un fichier de classe et nommez-le `FileAndContentTypes`.  
  
2. Ajoutez des références aux assemblys suivants :  
  
    1. System.ComponentModel.Composition  
  
    2. Microsoft.VisualStudio.Text.Logic  
  
    3. Microsoft.VisualStudio.CoreUtility  
  
3. Ajoutez le code suivant `using` directives.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4. Déclarez une classe statique qui contient les définitions.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5. Dans cette classe, exporter un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> nommé « masqué » et déclarer sa définition de base pour être « text ».  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Liaison d’une Extension de nom de fichier à un Type de contenu  
  
- Pour mapper ce type de contenu à une extension de nom de fichier, exporter un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> qui a l’extension « .hid » et le type de contenu « masqué ».  
  
    ```csharp  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Ajout du Type de contenu à une exportation de l’éditeur  
  
1. Créer une extension de l’éditeur. Par exemple, vous pouvez utiliser l’extension de glyphe de marge décrite dans [procédure pas à pas : Création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Ajoutez la classe que vous avez défini dans cette procédure.  
  
3. Lorsque vous exportez la classe d’extension, ajoutez un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de type « masqué » à ce dernier.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
