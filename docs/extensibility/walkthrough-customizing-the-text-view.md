---
title: 'Procédure pas à pas : personnalisation de l’affichage de texte | Microsoft Docs'
description: Découvrez comment personnaliser un affichage de texte en modifiant l’une des différentes propriétés dans son mappage de format d’éditeur à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ef4d0b408afc00a806e73d1e2eae7a07dde7814
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216850"
---
# <a name="walkthrough-customize-the-text-view"></a>Procédure pas à pas : personnaliser l’affichage du texte
Vous pouvez personnaliser un affichage de texte en modifiant l’une des propriétés suivantes dans sa carte de format d’éditeur :

- Marge des indicateurs

- Signe insertion

- Remplacer le signe insertion

- Texte sélectionné

- Texte sélectionné inactif (autrement dit, le texte sélectionné perd le focus)

- Espace blanc visible

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Créer un projet MEF

1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `ViewPropertyTest` .

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="define-the-content-type"></a>Définir le type de contenu

1. Ajoutez un fichier de classe et nommez-le `ViewPropertyModifier`.

2. Ajoutez les directives `using` suivantes :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. Déclarez une classe nommée `TestViewCreationListener` qui hérite de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exportez cette classe avec les attributs suivants :

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> pour spécifier le type de contenu auquel cet écouteur s’applique.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> pour spécifier le rôle de cet écouteur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. Dans cette classe, importez le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Modifier les propriétés de la vue

1. Configurez la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> méthode afin que les propriétés de la vue soient modifiées lorsque la vue est ouverte. Pour effectuer la modification, commencez par Rechercher le <xref:System.Windows.ResourceDictionary> qui correspond à l’aspect de la vue que vous souhaitez rechercher. Ensuite, modifiez la propriété appropriée dans le dictionnaire de ressources et définissez les propriétés. Traite les appels à la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> méthode en appelant la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> méthode avant de définir les propriétés, puis le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> après avoir défini les propriétés.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Générer et tester le code

1. Générez la solution.

     Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

2. Créez un fichier texte et tapez du texte.

    - Le signe insertion doit être magenta et le signe insertion de remplacement doit être turquoise.

    - La marge des indicateurs (à gauche de l’affichage de texte) doit être verte.

3. Sélectionnez le texte que vous avez tapé. La couleur du texte sélectionné doit être rose clair.

4. Lorsque le texte est sélectionné, cliquez n’importe où en dehors de la fenêtre de texte. La couleur du texte sélectionné doit être rose foncé.

5. Activez les espaces blancs visibles. (Dans le menu **Edition** , pointez sur **avancé** , puis cliquez sur Afficher les espaces **blancs**). Tapez certains onglets dans le texte. Les flèches rouges représentant les onglets doivent être affichées.

## <a name="see-also"></a>Voir aussi
- [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
