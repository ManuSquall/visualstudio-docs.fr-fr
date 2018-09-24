---
title: 'Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54570ec03788f88f58f14249f200ed2028686c37
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566751"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procédure pas à pas : Lier un type de contenu à une extension de nom de fichier
Vous pouvez définir votre propre type de contenu et lier une extension de nom de fichier en utilisant les extensions de Managed Extensibility Framework (MEF) de l’éditeur. Dans certains cas, l’extension de nom de fichier est déjà définie par un service de langage. Toutefois, pour l’utiliser avec MEF, vous devez toujours lier à un type de contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Créer un projet MEF  
  
1.  Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `ContentTypeTest`.  
  
2.  Dans le **source.extension.vsixmanifest** fichier, accédez à la **actifs** onglet et définissez le **Type** champ **Microsoft.VisualStudio.MefComponent**, le **Source** champ **un projet dans la solution actuelle**et le **projet** champ pour le nom du projet.  
  
## <a name="define-the-content-type"></a>Définir le type de contenu  
  
1.  Ajoutez un fichier de classe et nommez-le `FileAndContentTypes`.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Ajoutez le code suivant `using` directives.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Déclarez une classe statique qui contient les définitions.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Dans cette classe, exporter un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> nommé « masqué » et déclarer sa définition de base pour être « text ».  
  
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
  
-   Pour mapper ce type de contenu à une extension de nom de fichier, exporter un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> qui porte l’extension *.hid* et le type de contenu « masqué ».  
  
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
  
1.  Créer une extension de l’éditeur. Par exemple, vous pouvez utiliser l’extension de glyphe de marge décrite dans [procédure pas à pas : créer un glyphe de marge](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Ajoutez la classe que vous avez défini dans cette procédure.  
  
3.  Lorsque vous exportez la classe d’extension, ajoutez un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de type « masqué » à ce dernier.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension éditeur et le service de langage](../extensibility/language-service-and-editor-extension-points.md)