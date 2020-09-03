---
title: 'Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4e5ba3cd82090b5fad76d48c4600e0814bd91eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904680"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier
Vous pouvez définir votre propre type de contenu et y associer une extension de nom de fichier à l’aide des extensions Managed Extensibility Framework (MEF) de l’éditeur. Dans certains cas, l’extension de nom de fichier est déjà définie par un service de langage. Toutefois, pour l’utiliser avec MEF, vous devez toujours le lier à un type de contenu.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `ContentTypeTest` .

2. Dans le **fichier source. extension. vsixmanifest** , accédez à l’onglet **ressources** , définissez le champ **type** sur **Microsoft. VisualStudio. MEFComponent**, le champ **source** sur **un projet dans la solution actuelle**et le champ **projet** sur le nom du projet.

## <a name="define-the-content-type"></a>Définir le type de contenu

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

## <a name="link-a-file-name-extension-to-a-content-type"></a>Lier une extension de nom de fichier à un type de contenu

- Pour mapper ce type de contenu à une extension de nom de fichier, exportez un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> qui a l’extension *. HID* et le type de contenu « HID ».

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

## <a name="add-the-content-type-to-an-editor-export"></a>Ajouter le type de contenu à une exportation de l’éditeur

1. Créez une extension d’éditeur. Par exemple, vous pouvez utiliser l’extension de glyphe de marge décrite dans [procédure pas à pas : créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Ajoutez la classe que vous avez définie dans cette procédure.

3. Lorsque vous exportez la classe d’extension, ajoutez un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de type « HID » à celle-ci.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Voir aussi
- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
