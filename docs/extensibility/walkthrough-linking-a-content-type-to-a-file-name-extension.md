---
title: 'Procédure pas à pas : lier un type de contenu à une extension de nom de fichier (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697092"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procédure pas à pas : liez un type de contenu à une extension de nom de fichier
Vous pouvez définir votre propre type de contenu et y lier une extension de nom de fichier en utilisant les extensions du cadre d’extensibility gérée (MEF) de l’éditeur. Dans certains cas, l’extension du nom de fichier est déjà définie par un service linguistique. Mais, pour l’utiliser avec MEF, vous devez toujours le lier à un type de contenu.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `ContentTypeTest`la solution .

2. Dans le fichier **source.extension.vsixmanifest,** allez à l’onglet **Assets,** et définissez le champ **Type** à **Microsoft.VisualStudio.MefComponent**, le champ **Source** à **un projet en solution actuelle**, et le champ de **projet** au nom du projet.

## <a name="define-the-content-type"></a>Définir le type de contenu

1. Ajoutez un fichier de classe et nommez-le `FileAndContentTypes`.

2. Ajoutez des références aux assemblys suivants :

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic (en anglais seulement)

    3. Microsoft.VisualStudio.CoreUtility (en anglais seulement)

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

5. Dans cette catégorie, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> exporter un nommé "caché" et déclarer sa définition de base comme "texte".

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

- Pour cartographier ce type de contenu <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> à une extension de nom de fichier, exporter un qui a l’extension *.hid* et le type de contenu "caché".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Ajouter le type de contenu à une exportation d’éditeur

1. Créez une extension d’éditeur. Par exemple, vous pouvez utiliser l’extension de glyphe de marge décrite dans [Pasthrough: Créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Ajoutez la classe que vous avez définie dans cette procédure.

3. Lorsque vous exportez la <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> classe d’extension, ajoutez un type de «caché» à elle.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Voir aussi
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
