---
title: 'Procédure pas à pas : Personnaliser la vue sur le texte (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697469"
---
# <a name="walkthrough-customize-the-text-view"></a>Procédure pas à pas : Personnalisez la vue du texte
Vous pouvez personnaliser une vue de texte en modifiant l’une des propriétés suivantes dans sa carte de format éditeur :

- Marge des indicateurs

- Soins d’insertion

- Caret de surmort

- Texte sélectionné

- Texte sélectionné inactif (c’est-à-dire, texte sélectionné qui est mis au point)

- Espace blanc visible

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `ViewPropertyTest`la solution .

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="define-the-content-type"></a>Définir le type de contenu

1. Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.

2. Ajoutez les directives `using` suivantes :

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Déclarez une `TestViewCreationListener` classe nommée <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>qui hérite de . Exporter cette catégorie avec les attributs suivants:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>pour spécifier le type de contenu auquel cet auditeur s’applique.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>pour spécifier le rôle de cet auditeur.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. Dans cette classe, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>importer le .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Modifier les propriétés de vue

1. Configurez <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> la méthode afin que les propriétés de vue soient modifiées lorsque la vue est ouverte. Pour faire le changement, <xref:System.Windows.ResourceDictionary> d’abord trouver le qui correspond à l’aspect de la vue que vous voulez trouver. Ensuite, modifiez la propriété appropriée dans le dictionnaire des ressources et définissez les propriétés. Lotez les <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> appels vers <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> la méthode en appelant la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> méthode avant de définir les propriétés, puis après avoir réglé les propriétés.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Construire et tester le code

1. Générez la solution.

     Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

2. Créez un fichier texte et tapez du texte.

    - Le soin d’insertion doit être magenta et le caret de surballique doit être turquoise.

    - La marge d’indicateur (à gauche de la vue du texte) doit être vert clair.

3. Sélectionnez le texte que vous avez tapé. La couleur du texte sélectionné doit être rose clair.

4. Pendant que le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre de texte. La couleur du texte sélectionné doit être rose foncé.

5. Activez l’espace blanc visible. (Sur le menu **Edit,** pointez **vers Advanced** puis cliquez sur **Afficher l’espace blanc**). Tapez quelques onglets dans le texte. Les flèches rouges qui représentent les onglets doivent être affichées.

## <a name="see-also"></a>Voir aussi
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
