---
title: "Procédure pas à pas : Affichage de l’aide de Signature | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ced0eb5d3545a75ee31cff55d0e4fb9dab8c8bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-signature-help"></a>Procédure pas à pas : Affichage de l’aide de Signature
Aide pour la signature (également appelé *informations sur les paramètres*) affiche la signature d’une méthode dans une info-bulle lorsqu’un utilisateur tape le caractère de début de liste de paramètres (en général, une parenthèse ouvrante). Lorsqu’un paramètre et le séparateur de paramètre (en général une virgule) sont tapés, l’info-bulle est mise à jour pour afficher le paramètre suivant en gras. Vous pouvez définir l’aide de la Signature dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom du fichier et afficher l’aide de la Signature pour ce type, ou vous pouvez afficher l’aide de la Signature pour un type de contenu existant (par exemple, « text »). Cette procédure pas à pas montre comment afficher l’aide de la Signature pour le type de contenu « text ».  
  
 Aide pour la signature est généralement déclenché en tapant un caractère spécifique, par exemple, « (« (parenthèse ouvrante) et sera ignoré en tapant un autre caractère, par exemple, «) » (la parenthèse fermante). Les fonctionnalités IntelliSense qui sont déclenchées par la saisie d’un caractère peuvent être implémentées à l’aide d’un gestionnaire de commandes pour les séquences de touches (la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) et un fournisseur gestionnaire qui implémente le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source de l’aide de Signature, qui est la liste des signatures qui participent à l’aide de Signature, implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface et un fournisseur de source qui implémente le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. Les fournisseurs sont des composants de Managed Extensibility Framework (MEF) et est chargés d’exporter les classes source et le contrôleur et de l’importation de services et aux courtiers, par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui vous permet de vous naviguez dans la mémoire tampon de texte et la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, ce qui déclenche la session d’assistance de Signature.  
  
 Cette procédure pas à pas montre comment implémenter l’assistance de Signature pour un jeu codé en dur des identificateurs. Dans les implémentations complètes, la langue est chargée de fournir ce contenu.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Création d’un projet MEF  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet VSIX c#. (Dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual c# / extensibilité**, puis **projet VSIX**.) Nommez la solution `SignatureHelpTest`.  
  
2.  Ajouter un modèle d’élément classifieur d’éditeur pour le projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
4.  Ajoutez les références suivantes au projet et assurez-vous que **CopyLocal** a la valeur `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Assemblys Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Mise en œuvre de la Signature d’aider les Signatures et les paramètres  
 La source de l’aide de la Signature est basée sur les signatures qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, chacune contenant des paramètres qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Dans une implémentation complète, seraient obtenir ces informations à partir de la documentation de langage, mais dans cet exemple, les signatures sont codés en dur.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Pour implémenter les paramètres et les signatures d’assistance de Signature  
  
1.  Ajoutez un fichier de classe et nommez-le `SignatureHelpSource`.  
  
2.  Ajoutez les importations suivantes.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Ajoutez une classe nommée `TestParameter` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Ajoutez un constructeur qui définit toutes les propriétés.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Ajoutez les propriétés de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Ajoutez une classe nommée `TestSignature` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Ajoutez des champs privés.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Ajoutez un constructeur qui définit les champs et s’abonne à la <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Déclarez un `CurrentParameterChanged` événement. Cet événement est déclenché lorsque l’utilisateur remplit dans un des paramètres dans la signature.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implémentez la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propriété afin qu’elle déclenche le `CurrentParameterChanged` événement lorsque la valeur de propriété est modifiée.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Ajoutez une méthode qui déclenche le `CurrentParameterChanged` événement.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Ajoutez une méthode qui calcule le paramètre actuel en comparant le nombre de virgules dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> pour le nombre de virgules dans la signature.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Ajouter un gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement appelle le `ComputeCurrentParameter()` (méthode).  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implémentez la propriété <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Cette propriété contient un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> qui correspond à l’étendue de texte dans la mémoire tampon à laquelle s’applique la signature.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implémentez les autres paramètres.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Implémentation de la Source d’aide de Signature  
 La source de l’assistance de Signature est le jeu de signatures pour lequel vous fournissez des informations.  
  
#### <a name="to-implement-the-signature-help-source"></a>Pour implémenter la source de l’aide de la Signature  
  
1.  Ajoutez une classe nommée `TestSignatureHelpSource` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Ajoutez une référence à la mémoire tampon de texte.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Ajoutez un constructeur qui définit le fournisseur de source de l’aide de Signature et de la mémoire tampon de texte.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. Dans cet exemple, les signatures sont codés en dur, mais dans une implémentation complète, vous pourriez obtenir ces informations à partir de la documentation de langage.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  La méthode d’assistance `CreateSignature()` est fournie à des fins d’illustration uniquement.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. Dans cet exemple, il existe deux signatures, chacun d’eux possède deux paramètres. Par conséquent, cette méthode n’est pas requise. Dans une implémentation complète, dans lequel plusieurs sources d’assistance de Signature est disponible, cette méthode est utilisée pour déterminer si la source d’assistance de Signature de priorité la plus élevée peut fournir une signature correspondante. Si elle n’est pas le cas, la méthode retourne la valeur null et la source de la priorité la plus élevée suivante est invitée à fournir une correspondance.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implémentez la méthode Dispose() :  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implémentation du fournisseur de Source d’aide Signature  
 Le fournisseur de source de l’aide de Signature est chargé pour l’exportation de la partie du composant Managed Extensibility Framework (MEF) et pour l’instanciation de la source de l’aide de la Signature.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Pour implémenter le fournisseur de source de l’aide de Signature  
  
1.  Ajoutez une classe nommée `TestSignatureHelpSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>et l’exporter avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « texte » et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’avant = « default ».  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> en instanciant le `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Implémentation du Gestionnaire de commande  
 Aide pour la signature est généralement déclenché par un (caractère et ignorés par un) caractères. Vous pouvez gérer ces séquences de touches en implémentant un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> afin qu’il déclenche une session d’assistance de Signature lorsqu’elle reçoit un (caractère précédé par un nom de méthode connue et ferme la session lorsqu’il reçoit un) caractères.  
  
#### <a name="to-implement-the-command-handler"></a>Pour implémenter le Gestionnaire de commandes  
  
1.  Ajoutez une classe nommée `TestSignatureHelpCommand` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Ajoutez des champs privés pour le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> carte (ce qui vous permet d’ajouter le Gestionnaire de commandes pour les gestionnaires de la chaîne de commande), l’affichage de texte, l’assistance de Signature de service broker et la session, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>et l’autre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Ajoutez un constructeur pour initialiser ces champs et ajouter le filtre de commande pour les filtres de la chaîne de commande.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour déclencher la session d’assistance de Signature lorsque le filtre de commande reçoit une (caractère après l’un des noms de méthode connue et pour fermer la session lorsqu’il reçoit un) caractères alors que la session est toujours active. Dans tous les cas, la commande est transmise.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode afin qu’il transmet toujours la commande.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implémentation du fournisseur de commande aide Signature  
 Vous pouvez fournir la commande d’assistance de Signature en implémentant le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour instancier le Gestionnaire de commandes lors de la création de l’affichage de texte.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Pour implémenter le fournisseur de commande aide de la Signature  
  
1.  Ajoutez une classe nommée `TestSignatureHelpController` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> et l’exporter avec la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, et <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importation le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (utilisée pour obtenir le <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, étant donné la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet), la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (utilisé pour rechercher le mot en cours) et le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (pour déclencher la session d’assistance de Signature).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode en instanciant le `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution SignatureHelpTest et l’exécuter dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Pour générer et tester la solution SignatureHelpTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créer un fichier texte et du texte qui inclut le mot « ajouter » de type et une parenthèse ouvrante.  
  
4.  Une fois que vous tapez la parenthèse ouvrante, vous devez voir une info-bulle qui affiche une liste des deux signatures pour le `add()` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)