---
title: 'Procédure pas à pas : affichage de l’aide sur la signature | Microsoft Docs'
description: Découvrez comment afficher l’aide sur les signatures pour le type de contenu texte à l’aide de cette procédure pas à pas. L’aide sur la signature affiche la signature d’une méthode dans une info-bulle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8933822ee5bb63b341ff51296ba2884fef2aeb75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935909"
---
# <a name="walkthrough-display-signature-help"></a>Procédure pas à pas : afficher l’aide sur les signatures
L’aide sur la signature (également appelée *informations sur les paramètres*) affiche la signature d’une méthode dans une info-bulle lorsqu’un utilisateur tape le caractère de début de liste de paramètres (généralement une parenthèse ouvrante). Comme un paramètre et un séparateur de paramètres (généralement une virgule) sont tapés, l’info-bulle est mise à jour pour afficher le paramètre suivant en gras. Vous pouvez définir l’aide de la signature des manières suivantes : dans le contexte d’un service de langage, définissez votre propre extension de nom de fichier et le type de contenu, ainsi que la signature d’affichage pour ce type, ou affichez l’aide de signature pour un type de contenu existant (par exemple, « texte »). Cette procédure pas à pas montre comment afficher l’aide sur la signature pour le type de contenu « text ».

 L’assistance de signature est généralement déclenchée par la saisie d’un caractère spécifique, par exemple, « ( » (parenthèse ouvrante) et ignorée en tapant un autre caractère, par exemple « ) » (parenthèse fermante). Les fonctionnalités IntelliSense qui sont déclenchées en tapant un caractère peuvent être implémentées à l’aide d’un gestionnaire de commandes pour les séquences de touches (l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) et d’un fournisseur de gestionnaires qui implémente l' <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source d’assistance de signature, qui est la liste des signatures qui participent à l’assistance de signature, implémentez l' <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface et un fournisseur de source qui exécute l' <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. Les fournisseurs sont des composants de Managed Extensibility Framework (MEF) et sont responsables de l’exportation des classes source et contrôleur et de l’importation des services et des courtiers, par exemple,, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> qui vous permet de naviguer dans la mémoire tampon de texte, et <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , qui déclenche la session d’assistance de signature.

 Cette procédure pas à pas montre comment configurer l’aide sur la signature pour un ensemble d’identificateurs codés en dur. Dans les implémentations complètes, le langage est chargé de fournir ce contenu.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Création d’un projet MEF

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet VSIX C#. (Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#/extensibilité**, puis **projet VSIX**.) Nommez la solution `SignatureHelpTest` .

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez les références suivantes au projet et assurez-vous que **CopyLocal** a la valeur `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implémenter des signatures et des paramètres d’assistance de signature
 La source d’assistance de signature est basée sur les signatures qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , chacune contenant des paramètres qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . Dans une implémentation complète, ces informations seraient obtenues à partir de la documentation du langage, mais dans cet exemple, les signatures sont codées en dur.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Pour implémenter les signatures et les paramètres d’aide de signature

1. Ajoutez un fichier de classe et nommez-le `SignatureHelpSource`.

2. Ajoutez les importations suivantes.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Ajoutez une classe nommée `TestParameter` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Ajoutez un constructeur qui définit toutes les propriétés.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Ajoutez les propriétés de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Ajoutez une classe nommée `TestSignature` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Ajoutez des champs privés.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Ajoutez un constructeur qui définit les champs et s’abonne à l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Déclarez un `CurrentParameterChanged` événement. Cet événement est déclenché lorsque l’utilisateur remplit l’un des paramètres dans la signature.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propriété pour qu’elle déclenche l' `CurrentParameterChanged` événement lorsque la valeur de propriété est modifiée.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Ajoutez une méthode qui déclenche l' `CurrentParameterChanged` événement.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Ajoutez une méthode qui calcule le paramètre actuel en comparant le nombre de virgules dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> au nombre de virgules dans la signature.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Ajoutez un gestionnaire d’événements pour l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement qui appelle la `ComputeCurrentParameter()` méthode.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implémentez la propriété <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Cette propriété contient un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> qui correspond à l’étendue de texte de la mémoire tampon à laquelle la signature s’applique.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implémentez les autres paramètres.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implémenter la source d’assistance de signature
 La source d’assistance de signature est l’ensemble des signatures pour lesquelles vous fournissez des informations.

#### <a name="to-implement-the-signature-help-source"></a>Pour implémenter la source d’assistance de signature

1. Ajoutez une classe nommée `TestSignatureHelpSource` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Ajoutez une référence à la mémoire tampon de texte.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Ajoutez un constructeur qui définit la mémoire tampon de texte et le fournisseur de sources d’assistance de signature.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. Dans cet exemple, les signatures sont codées en dur, mais dans une implémentation complète, vous obtiendriez ces informations à partir de la documentation du langage.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. La méthode d’assistance `CreateSignature()` est fournie uniquement à titre d’illustration.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. Dans cet exemple, il existe seulement deux signatures, chacune ayant deux paramètres. Par conséquent, cette méthode n’est pas obligatoire. Dans une implémentation plus complète, dans laquelle plusieurs sources d’aide de signature sont disponibles, cette méthode est utilisée pour déterminer si la source d’aide de signature la plus haute priorité peut fournir une signature correspondante. Si ce n’est pas le cas, la méthode retourne null et la source de priorité la plus élevée est invitée à fournir une correspondance.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implémentez la `Dispose()` méthode :

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implémenter le fournisseur de sources d’assistance de signature
 Le fournisseur de sources d’assistance de signature est chargé d’exporter la partie du composant Managed Extensibility Framework (MEF) et d’instancier la source d’assistance de signature.

#### <a name="to-implement-the-signature-help-source-provider"></a>Pour implémenter le fournisseur de sources d’assistance de signature

1. Ajoutez une classe nommée `TestSignatureHelpSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , puis exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « Text » et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = « default ».

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> en instanciant le `TestSignatureHelpSource` .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implémenter le gestionnaire de commandes
 L’assistance de signature est généralement déclenchée par une parenthèse ouvrante « ( » et est ignorée par un caractère de parenthèse fermante « ) ». Vous pouvez gérer ces séquences de touches en exécutant un de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sorte qu’il déclenche une session d’assistance de signature lorsqu’il reçoit un caractère de parenthèse ouvrante précédé d’un nom de méthode connu et ferme la session lorsqu’elle reçoit un caractère de parenthèse fermante.

#### <a name="to-implement-the-command-handler"></a>Pour implémenter le gestionnaire de commandes

1. Ajoutez une classe nommée `TestSignatureHelpCommand` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Ajoutez des champs privés pour l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptateur (ce qui vous permet d’ajouter le gestionnaire de commandes à la chaîne de gestionnaires de commandes), l’affichage de texte, la signature Help Broker et session, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> et la suivante <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Ajoutez un constructeur pour initialiser ces champs et ajouter le filtre de commande à la chaîne de filtres de commande.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour déclencher la session d’assistance de signature lorsque le filtre de commande reçoit une parenthèse ouvrante « ( » après l’un des noms de méthodes connus, et pour faire disparaître la session lorsqu’elle reçoit un caractère « » » de parenthèse fermante alors que la session est toujours active. Dans tous les cas, la commande est transférée.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode afin qu’elle transfère toujours la commande.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implémenter le fournisseur de commandes d’assistance de signature
 Vous pouvez fournir la commande d’assistance de signature en implémentant le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour instancier le gestionnaire de commandes lorsque l’affichage de texte est créé.

### <a name="to-implement-the-signature-help-command-provider"></a>Pour implémenter le fournisseur de commandes d’assistance de signature

1. Ajoutez une classe nommée `TestSignatureHelpController` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> et exportez-la avec les <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> et <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importez le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (utilisé pour obtenir le <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , en fonction de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet), le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (utilisé pour rechercher le mot actuel) et le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pour déclencher la session d’assistance de signature).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implémentez la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode en instanciant le `TestSignatureCommandHandler` .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution SignatureHelpTest et exécutez-la dans l’instance expérimentale.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Pour générer et tester la solution SignatureHelpTest

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et tapez du texte qui contient le mot « Add » plus une parenthèse ouvrante.

4. Une fois que vous avez tapé la parenthèse ouvrante, vous devez voir une info-bulle qui affiche la liste des deux signatures de la `add()` méthode.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
