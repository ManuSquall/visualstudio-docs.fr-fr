---
title: 'Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201992"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir votre propre type de contenu et y associer une extension de nom de fichier à l’aide des extensions de l’éditeur Managed Extensibility Framework (MEF). Dans certains cas, l’extension de nom de fichier a déjà été définie par un service de langage. Toutefois, pour l’utiliser avec MEF, vous devez toujours le lier à un type de contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `ContentTypeTest` .  
  
2. Dans le **fichier source. extension. vsixmanifest** , accédez à l’onglet **ressources** , définissez le champ **type** sur **Microsoft. VisualStudio. MEFComponent**, le champ **source** sur **un projet dans la solution actuelle**et le champ **projet** sur le nom du projet.  
  
## <a name="defining-the-content-type"></a>Définition du type de contenu  
  
1. Ajoutez un fichier de classe et nommez-le `FileAndContentTypes`.  
  
2. Ajoutez des références aux assemblys suivants :  
  
    1. System.ComponentModel.Composition  
  
    2. Microsoft. VisualStudio. Text. Logic  
  
    3. Microsoft. VisualStudio. CoreUtility  
  
3. Ajoutez les `using` directives suivantes.  
  
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
  
5. Dans cette classe, exportez un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> nommé « HID » et déclarez sa définition de base comme étant « Text ».  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Liaison d’une extension de nom de fichier à un type de contenu  
  
- Pour mapper ce type de contenu à une extension de nom de fichier, exportez un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> qui a l’extension « . HID » et le type de contenu « HID ».  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Ajout du type de contenu à une exportation de l’éditeur  
  
1. Créez une extension d’éditeur. Par exemple, vous pouvez utiliser l’extension de glyphe de marge décrite dans [procédure pas à pas : création d’un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Ajoutez la classe que vous avez définie dans cette procédure.  
  
3. Lorsque vous exportez la classe d’extension, ajoutez un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de type « HID » à celle-ci.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
