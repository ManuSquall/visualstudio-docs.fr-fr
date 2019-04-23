---
title: 'Procédure pas à pas : Affichage de l’aide de la Signature | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d81ee2e860dead62352cc14cef95e21536c29d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105318"
---
# <a name="walkthrough-display-signature-help"></a>Procédure pas à pas : Afficher l’aide de la Signature
Pour la signature (également appelé *informations sur les paramètres*) affiche la signature d’une méthode dans une info-bulle lorsqu’un utilisateur tape le caractère de début de liste de paramètre (généralement une parenthèse ouvrante). Lorsqu’un paramètre et le séparateur de paramètre (en général une virgule) sont tapés, l’info-bulle est mise à jour pour afficher le paramètre suivant en gras. Vous pouvez définir l’assistance de Signature comme suit : dans le contexte d’un service de langage, définir votre propre extension de nom de fichier et le type de contenu et afficher l’aide de la Signature pour uniquement ce type ou afficher l’aide de la Signature pour un type de contenu existant (par exemple, « texte »). Cette procédure pas à pas montre comment afficher l’aide de la Signature pour le type de contenu « texte ».

 Pour la signature est généralement déclenchée en tapant un caractère spécifique, par exemple, « (« (parenthèse ouvrante) et sera ignoré en tapant un autre caractère, par exemple, «) » (la parenthèse fermante). Les fonctionnalités IntelliSense qui sont déclenchées en tapant un caractère peuvent être implémentées à l’aide d’un gestionnaire de commandes pour les séquences de touches (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) et un fournisseur de gestionnaire qui implémente le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source d’aide pour la Signature, qui est la liste des signatures qui participent à l’aide de Signature, implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface et un fournisseur de code source qui exécute le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. Les fournisseurs sont des composants de Managed Extensibility Framework (MEF) et sont responsables pour exporter les classes source et de contrôleur et importer des services et des courtiers, par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui vous permet de naviguer dans la mémoire tampon de texte et le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, ce qui déclenche la session d’assistance de Signature.

 Cette procédure pas à pas montre comment configurer d’assistance de Signature pour un ensemble codées en dur des identificateurs. Dans les implémentations complètes, le langage est chargé de fournir ce contenu.

## <a name="prerequisites"></a>Prérequis
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Création d’un projet MEF

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet c# VSIX. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `SignatureHelpTest`.

2. Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez les références suivantes au projet et assurez-vous que **CopyLocal** est défini sur `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implémenter des signatures d’assistance de Signature et de paramètres
 La source de l’assistance de Signature est basée sur les signatures qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, chacune contenant des paramètres qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Dans une implémentation complète, ces informations seraient être obtenues à partir de la documentation du langage, mais dans cet exemple, les signatures sont codées en dur.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Pour implémenter les signatures d’assistance de Signature et les paramètres

1. Ajoutez un fichier de classe et nommez-le `SignatureHelpSource`.

2. Ajoutez les importations ci-après.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Ajoutez une classe nommée `TestParameter` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Ajoutez un constructeur qui définit toutes les propriétés.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Ajoutez les propriétés de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Ajoutez une classe nommée `TestSignature` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Ajouter des champs privés.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Ajoutez un constructeur qui définit les champs et s’abonne à la <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Déclarez un `CurrentParameterChanged` événement. Cet événement est déclenché lorsque l’utilisateur remplit dans l’un des paramètres dans la signature.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propriété afin qu’elle déclenche le `CurrentParameterChanged` événement lorsque la valeur de propriété est modifiée.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Ajoutez une méthode qui déclenche le `CurrentParameterChanged` événement.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Ajoutez une méthode qui calcule le paramètre actuel en comparant le nombre de virgules dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> au nombre de virgules dans la signature.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Ajouter un gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement appelle le `ComputeCurrentParameter()` (méthode).

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implémentez la propriété <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Cette propriété contient un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> qui correspond à l’étendue de texte dans la mémoire tampon à laquelle s’applique la signature.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implémenter les autres paramètres.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Mettre en œuvre de la source de l’assistance de Signature
 La source de l’assistance de Signature est le jeu de signatures pour lequel vous fournissez des informations.

#### <a name="to-implement-the-signature-help-source"></a>Pour implémenter la source d’assistance de Signature

1. Ajoutez une classe nommée `TestSignatureHelpSource` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Ajoutez une référence à la mémoire tampon de texte.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Ajoutez un constructeur qui définit la mémoire tampon de texte et le fournisseur aide pour la Signature de code source.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. Dans cet exemple, les signatures sont codées en dur, mais dans une implémentation complète, vous obtiendriez ces informations à partir de la documentation du langage.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. La méthode d’assistance `CreateSignature()` est fourni uniquement à titre d’illustration.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. Dans cet exemple, il existe seulement deux signatures, chacun d’eux a deux paramètres. Par conséquent, cette méthode n’est pas requise. Dans une implémentation plus complète, dans lequel plusieurs sources d’aide pour la Signature est disponible, cette méthode est utilisée pour déterminer si la source d’aide pour la Signature de priorité la plus élevée peut fournir une signature correspondante. S’il ne peut pas, la méthode retourne la valeur null et la source de la priorité la plus élevée suivante est invitée à fournir une correspondance.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implémentez la `Dispose()` méthode :

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implémenter le fournisseur aide pour la Signature de code source
 Le fournisseur aide pour la Signature de code source est chargé pour l’exportation de la partie du composant Managed Extensibility Framework (MEF) et de l’instanciation de la source de l’assistance de Signature.

#### <a name="to-implement-the-signature-help-source-provider"></a>Pour implémenter le fournisseur aide pour la Signature de code source

1. Ajoutez une classe nommée `TestSignatureHelpSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>et exportez-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « text » et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’avant = « default ».

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> en instanciant le `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implémenter le Gestionnaire de commandes
 Pour la signature est généralement déclenchée par une parenthèse ouvrante caractère « (« caractère et rejeté par une parenthèse fermante «) ». Vous pouvez gérer ces séquences de touches en exécutant un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> afin qu’il déclenche une session d’assistance de Signature lorsqu’elle reçoit une ouverture de caractère de parenthèse précédé par un nom de méthode connue et ferme la session lorsqu’elle reçoit une fermeture de parenthèse fermante.

#### <a name="to-implement-the-command-handler"></a>Pour implémenter le Gestionnaire de commandes

1. Ajoutez une classe nommée `TestSignatureHelpCommand` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Ajouter des champs privés pour le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptateur (ce qui vous permet d’ajouter le Gestionnaire de commandes pour les gestionnaires de la chaîne de commande), l’affichage de texte, l’assistance de Signature de broker et la session, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>et l’autre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Ajoutez un constructeur pour initialiser ces champs et ajouter le filtre de commande à la chaîne de filtres de commande.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour déclencher la session d’assistance de Signature lorsque le filtre de commande reçoit une parenthèse ouvrante caractère « (« caractère après l’un des noms de méthode connue et pour fermer la session lorsqu’elle reçoit une parenthèse fermante «) » Lorsque la session est toujours active. Dans tous les cas, la commande est transférée.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode afin qu’il transfère toujours la commande.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implémenter le fournisseur de commande aide pour la Signature
 Vous pouvez fournir la commande d’assistance de Signature en implémentant le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour instancier le Gestionnaire de commandes lors de la création de l’affichage de texte.

### <a name="to-implement-the-signature-help-command-provider"></a>Pour implémenter le fournisseur de commande aide pour la Signature

1. Ajoutez une classe nommée `TestSignatureHelpController` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> et exportez-le avec la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, et <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (permettant d’obtenir le <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, à partir la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet), la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (utilisé pour rechercher le mot actuel) et le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pour déclencher la session d’assistance de Signature).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implémentez le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode en instanciant le `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Générer et tester le Code
 Pour tester ce code, générez la solution SignatureHelpTest et exécutez-le dans l’instance expérimentale.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Pour générer et tester la solution SignatureHelpTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créez un fichier texte et du texte qui inclut le mot « ajouter » de type plus une parenthèse ouvrante.

4. Une fois que vous tapez la parenthèse ouvrante, vous devez voir une info-bulle qui affiche une liste des deux signatures pour le `add()` (méthode).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Lier un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)