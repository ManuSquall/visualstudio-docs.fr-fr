---
title: 'Procédure pas à pas : Afficher l’aide signature Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697418"
---
# <a name="walkthrough-display-signature-help"></a>Procédure pas à pas : Offrez l’aide signature d’affichage
Signature Help (également connu sous le nom *de Para Info*) affiche la signature d’une méthode dans un tooltip lorsqu’un utilisateur tape le caractère de début de liste de paramètres (généralement une parenthèse d’ouverture). Comme un paramètre et un séparateur de paramètre (généralement une virgule) sont tapés, l’outil est mis à jour pour afficher le paramètre suivant en gras. Vous pouvez définir l’aide signature de la manière suivante : dans le cadre d’un service linguistique, définissez votre propre extension de nom de fichier et type de contenu et affichez l’aide signature pour ce type, ou affichez l’aide signature pour un type de contenu existant (par exemple, « texte »). Ce pas-là montre comment afficher l’aide signature pour le type de contenu "texte".

 Signature Help est généralement déclenchée par la dactylographie d’un personnage spécifique, par exemple, "(" (parenthèse d’ouverture), et rejeté en tapant un autre personnage, par exemple, ")" (parenthèse de fermeture). Les fonctionnalités IntelliSense qui sont déclenchées par la saisie d’un personnage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> peuvent être implémentées <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> en utilisant un gestionnaire de commande pour les frappes (l’interface) et un fournisseur de gestionnaire qui implémente l’interface. Pour créer la source d’aide signature, qui est la liste <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> des signatures qui <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> participent à Signature Help, implémentez l’interface et un fournisseur source qui exécute l’interface. Les fournisseurs sont gérés Extensibility Framework (MEF) parties composant, et sont responsables de l’exportation des <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>classes source et contrôleur et les <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>services d’importation et les courtiers, par exemple, le , qui vous permet de naviguer dans le tampon de texte, et le , qui déclenche la session d’aide signature.

 Ce pas-fort montre comment configurer Signature Help pour un ensemble d’identifiants codés en dur. Dans les implémentations complètes, la langue est responsable de fournir ce contenu.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Création d’un projet MEF

#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet VSIX CMD. (Dans le dialogue du **nouveau projet,** sélectionnez **Visual C / Extensibility**, puis **VSIX Project**.) Nommez `SignatureHelpTest`la solution .

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

4. Ajoutez les références suivantes au projet et assurez-vous `false`que **CopyLocal** est configuré à :

     Microsoft.VisualStudio.Éditeur

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Mettre en œuvre les signatures et les paramètres de Signature Help
 La source d’aide signature est <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>basée sur les signatures <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>qui implémentent , chacune d’entre elles contient des paramètres qui implémentent . Dans une mise en œuvre complète, ces informations seraient obtenues à partir de la documentation linguistique, mais dans cet exemple, les signatures sont codées en dur.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Mettre en œuvre les signatures et paramètres De Signature Help

1. Ajoutez un fichier de classe et nommez-le `SignatureHelpSource`.

2. Ajoutez les importations suivantes.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Ajouter une `TestParameter` classe nommée <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>qui implémente .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Ajouter un constructeur qui définit toutes les propriétés.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Ajouter les <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>propriétés de .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Ajouter une `TestSignature` classe nommée <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>qui implémente .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Ajoutez quelques champs privés.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Ajoutez un constructeur qui définit les champs <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> et s’abonner à l’événement.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Déclarez `CurrentParameterChanged` un événement. Cet événement est soulevé lorsque l’utilisateur remplit l’un des paramètres de la signature.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Mettre <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> en œuvre `CurrentParameterChanged` la propriété de sorte qu’il soulève l’événement lorsque la valeur de la propriété est modifiée.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Ajoutez une méthode `CurrentParameterChanged` qui soulève l’événement.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Ajoutez une méthode qui calcule le paramètre actuel en <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> comparant le nombre de virgules dans le nombre de virgules dans la signature.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Ajoutez un gestionnaire <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> d’événements `ComputeCurrentParameter()` pour l’événement qui appelle la méthode.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implémentez la propriété <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Cette propriété <xref:Microsoft.VisualStudio.Text.ITrackingSpan> contient un qui correspond à la durée du texte dans le tampon auquel la signature s’applique.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implémenter les autres paramètres.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Mettre en œuvre la source d’aide signature
 La source d’aide signature est l’ensemble de signatures pour lesquelles vous fournissez des informations.

#### <a name="to-implement-the-signature-help-source"></a>Pour implémenter la source d’aide signature

1. Ajouter une `TestSignatureHelpSource` classe nommée <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>qui implémente .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Ajoutez une référence au tampon de texte.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Ajoutez un constructeur qui définit le tampon de texte et le fournisseur de source d’aide signature.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. Dans cet exemple, les signatures sont codées par des durs, mais dans une implémentation complète, vous obtiendriez cette information à partir de la documentation linguistique.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. La méthode `CreateSignature()` d’aide est fournie juste pour l’illustration.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. Dans cet exemple, il n’y a que deux signatures, dont chacune comporte deux paramètres. Par conséquent, cette méthode n’est pas nécessaire. Dans une implémentation plus complète, dans laquelle plus d’une source d’aide signature est disponible, cette méthode est utilisée pour décider si la source d’aide signature la plus prioritaire peut fournir une signature correspondante. Si ce n’est pas le cas, la méthode revient nulle et la prochaine source prioritaire est priée de fournir une correspondance.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Mettre `Dispose()` en œuvre la méthode :

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Mettre en œuvre le fournisseur de source d’aide signature
 Le fournisseur source Signature Help est responsable de l’exportation de la partie composante du Cadre d’exténuabilité gérée (MEF) et de l’instantanéise de la source d’aide signature.

#### <a name="to-implement-the-signature-help-source-provider"></a>Pour implémenter le fournisseur de source d’aide signature

1. Ajoutez une `TestSignatureHelpSourceProvider` classe nommée <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>qui implémente, et exportez-la avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> « texte » et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> « défaut » d’Avant.

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implémenter <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> en `TestSignatureHelpSource`instantanéisant le .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Mettre en œuvre le gestionnaire de commande
 Signature Help est généralement déclenchée par une parenthèse d’ouverture "(" caractère et rejeté par une parenthèse de clôture ")" caractère. Vous pouvez gérer ces frappes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> en exécutant un de sorte qu’il déclenche une session d’aide signature quand il reçoit un personnage de parenthèse d’ouverture précédé d’un nom de méthode connu, et rejette la session quand il reçoit un caractère de parenthèse de clôture.

#### <a name="to-implement-the-command-handler"></a>Pour mettre en œuvre le gestionnaire de commande

1. Ajouter une `TestSignatureHelpCommand` classe nommée <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>qui implémente .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Ajoutez des champs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> privés pour l’adaptateur (qui vous permet d’ajouter le gestionnaire de commande <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>à la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>chaîne de gestionnaires de commande), la vue de texte, le courtier et la session Signature Help, un , et le suivant .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Ajoutez un constructeur pour initialiser ces champs et ajouter le filtre de commande à la chaîne de filtres de commande.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour déclencher la session d’aide à la signature lorsque le filtre de commande reçoit un caractère d’ouverture de parenthèse « (» après l’un des noms de méthode connus, et pour rejeter la session lorsqu’il reçoit une parenthèse de clôture «)» caractère pendant que la session est toujours active. Dans tous les cas, la commande est transmise.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode de sorte qu’elle avance toujours la commande.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Mettre en œuvre le fournisseur de commande d’aide signature
 Vous pouvez fournir la commande d’aide signature en implémentant le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> gestionnaire de commande instantané lorsque la vue de texte est créée.

### <a name="to-implement-the-signature-help-command-provider"></a>Pour implémenter le fournisseur de commande Signature Help

1. Ajouter une `TestSignatureHelpController` classe nommée <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> qui met <xref:Microsoft.VisualStudio.Utilities.NameAttribute>en <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>œuvre et l’exporter avec le , , et <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importer <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> le (utilisé <xref:Microsoft.VisualStudio.Text.Editor.ITextView>pour obtenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , étant donné l’objet), <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> le (utilisé pour trouver le mot actuel), et le (pour déclencher la session d’aide signature).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implémenter la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode `TestSignatureCommandHandler`en instantanéisant le .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Construire et tester le Code
 Pour tester ce code, créez la solution SignatureHelpTest et exécutez-la dans le cas expérimental.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Construire et tester la solution SignatureHelpTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créez un fichier texte et tapez du texte qui inclut le mot « ajouter » plus une parenthèse d’ouverture.

4. Après avoir tapé la parenthèse d’ouverture, vous devriez voir un tooltip qui affiche une liste des deux signatures pour la `add()` méthode.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
