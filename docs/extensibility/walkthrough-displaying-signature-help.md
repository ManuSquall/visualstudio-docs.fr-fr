---
title: "Proc&#233;dure pas &#224; pas&#160;: Affichage de l’aide de Signature | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - informations sur les signatures aide/paramètre"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Proc&#233;dure pas &#224; pas&#160;: Affichage de l’aide de Signature
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aide pour la signature \(également appelé *informations sur les paramètres*\) affiche la signature d’une méthode dans une info\-bulle lorsqu’un utilisateur tape le caractère de début de liste paramètre \(généralement une parenthèse ouvrante\). Comme un paramètre et un séparateur de paramètre \(en général une virgule\) sont typées, l’info\-bulle est mise à jour pour afficher le paramètre suivant en gras. Vous pouvez définir l’assistance de Signature dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom fichier et afficher l’aide de la Signature de ce type, ou vous pouvez afficher l’assistance de Signature pour un type de contenu existant \(par exemple, « texte »\). Cette procédure pas à pas montre comment afficher l’aide de la Signature pour le type de contenu « texte ».  
  
 Aide pour la signature est généralement déclenché en tapant un caractère spécifique, par exemple, « \( » \(parenthèse ouvrante\) et sera ignoré en tapant un autre caractère, par exemple, «\) » \(la parenthèse fermante\). Les fonctionnalités IntelliSense qui sont déclenchées en tapant un caractère peuvent être implémentées à l’aide d’un gestionnaire de commandes pour les séquences de touches \(la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface\) et un fournisseur de gestionnaire qui implémente le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Pour créer la source d’assistance de Signature, qui est la liste des signatures qui participent à l’aide de Signature, implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface et un fournisseur de code source qui implémente le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. Les fournisseurs sont des composants de Managed Extensibility Framework \(MEF\) et sont chargés pour exporter les classes source et le contrôleur et importer des services et des courtiers, par exemple, le <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, qui vous permet de naviguer dans la mémoire tampon de texte et le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, ce qui déclenche la session d’assistance de Signature.  
  
 Cette procédure pas à pas montre comment implémenter l’assistance de Signature pour un jeu codé en dur des identificateurs. Dans les implémentations complètes, le langage est chargé de fournir ce contenu.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’un projet MEF  
  
#### Pour créer un projet MEF  
  
1.  Créez un projet VSIX c\#. \(Dans le **Nouveau projet** boîte de dialogue, sélectionnez **Visual C\# \/ extensibilité**, puis **projet VSIX**.\) Nommez la solution `SignatureHelpTest`.  
  
2.  Ajouter un modèle d’élément éditeur classifieur au projet. Pour plus d'informations, consultez [Création d'une Extension avec un éditeur de modèle d'élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
4.  Ajoutez les références suivantes au projet et assurez\-vous que **CopyLocal** est défini sur `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Assemblys Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## L’implémentation de Signature aide les Signatures et les paramètres  
 La source de l’assistance de Signature est basée sur les signatures qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, dont chacun contient des paramètres qui implémentent <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. Dans une implémentation complète, ces informations seraient être obtenues à partir de la documentation de langage, mais dans cet exemple, les signatures sont codées en dur.  
  
#### Pour implémenter les paramètres et les signatures d’assistance de Signature  
  
1.  Ajoutez un fichier de classe et nommez\-le `SignatureHelpSource`.  
  
2.  Ajoutez les importations ci\-après.  
  
     [!CODE [VSSDKSignatureHelpTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#1)]  
  
3.  Ajoutez une classe nommée `TestParameter` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!CODE [VSSDKSignatureHelpTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#2)]  
  
4.  Ajoutez un constructeur qui définit toutes les propriétés.  
  
     [!CODE [VSSDKSignatureHelpTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#3)]  
  
5.  Ajoutez les propriétés de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!CODE [VSSDKSignatureHelpTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#4)]  
  
6.  Ajoutez une classe nommée `TestSignature` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!CODE [VSSDKSignatureHelpTest#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#5)]  
  
7.  Ajoutez des champs privés.  
  
     [!CODE [VSSDKSignatureHelpTest#6](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#6)]  
  
8.  Ajoutez un constructeur qui définit les champs et s’abonne à la <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
     [!CODE [VSSDKSignatureHelpTest#7](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#7)]  
  
9. Déclarez un `CurrentParameterChanged` événement. Cet événement est déclenché lorsque l’utilisateur remplit dans l’un des paramètres dans la signature.  
  
     [!CODE [VSSDKSignatureHelpTest#8](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#8)]  
  
10. Implémentez le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propriété afin qu’elle déclenche le `CurrentParameterChanged` événement lorsque la valeur de propriété est modifiée.  
  
     [!CODE [VSSDKSignatureHelpTest#9](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#9)]  
  
11. Ajoutez une méthode qui déclenche le `CurrentParameterChanged` événement.  
  
     [!CODE [VSSDKSignatureHelpTest#10](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#10)]  
  
12. Ajoutez une méthode qui calcule le paramètre actuel en comparant le nombre de virgules dans le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> pour le nombre de virgules dans la signature.  
  
     [!CODE [VSSDKSignatureHelpTest#11](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#11)]  
  
13. Ajoutez un gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement appelle le `ComputeCurrentParameter()` \(méthode\).  
  
     [!CODE [VSSDKSignatureHelpTest#12](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#12)]  
  
14. Implémentez la propriété <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Cette propriété contient un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> qui correspond à l’étendue de texte dans la mémoire tampon auquel s’applique la signature.  
  
     [!CODE [VSSDKSignatureHelpTest#13](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#13)]  
  
15. Implémentez les autres paramètres.  
  
     [!CODE [VSSDKSignatureHelpTest#14](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#14)]  
  
## L’implémentation de la Source d’aide de Signature  
 La source de l’assistance de Signature est le jeu de signatures pour lequel vous fournissez des informations.  
  
#### Pour implémenter la source de l’assistance de Signature  
  
1.  Ajoutez une classe nommée `TestSignatureHelpSource` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!CODE [VSSDKSignatureHelpTest#15](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#15)]  
  
2.  Ajoutez une référence à la mémoire tampon de texte.  
  
     [!CODE [VSSDKSignatureHelpTest#16](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#16)]  
  
3.  Ajoutez un constructeur qui définit la mémoire tampon de texte et le fournisseur assistance de Signature de code source.  
  
     [!CODE [VSSDKSignatureHelpTest#17](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#17)]  
  
4.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. Dans cet exemple, les signatures sont codées en dur, mais dans une implémentation complète, vous obtiendriez ces informations à partir de la documentation de langage.  
  
     [!CODE [VSSDKSignatureHelpTest#18](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#18)]  
  
5.  La méthode d’assistance `CreateSignature()` est fourni uniquement à titre d’illustration.  
  
     [!CODE [VSSDKSignatureHelpTest#19](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#19)]  
  
6.  Implémentez la méthode <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. Dans cet exemple, il existe seulement deux signatures, chacune d’elles possède deux paramètres. Par conséquent, cette méthode n’est pas requise. Dans une implémentation plus complète, dans laquelle plusieurs sources d’assistance de Signature est disponible, cette méthode est utilisée pour déterminer si la source d’assistance de Signature de priorité la plus élevée peut fournir une signature correspondante. Si elle n’est pas le cas, la méthode retourne la valeur null et la source de la priorité la plus élevée suivante est invitée à fournir une correspondance.  
  
     [!CODE [VSSDKSignatureHelpTest#20](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#20)]  
  
7.  Implémentez la méthode Dispose\(\) :  
  
     [!CODE [VSSDKSignatureHelpTest#21](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#21)]  
  
## Implémentation du fournisseur de Source d’aide Signature  
 Le fournisseur de source assistance de Signature est chargé pour l’exportation de la partie du composant Managed Extensibility Framework \(MEF\) et à l’instanciation de la source de l’assistance de Signature.  
  
#### Pour implémenter le fournisseur d’assistance de Signature source  
  
1.  Ajoutez une classe nommée `TestSignatureHelpSourceProvider` qui implémente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, et exportez\-le avec un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de « text » et un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> d’avant \= « default ».  
  
     [!CODE [VSSDKSignatureHelpTest#22](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#22)]  
  
2.  Implémentez <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> en instanciant le `TestSignatureHelpSource`.  
  
     [!CODE [VSSDKSignatureHelpTest#23](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#23)]  
  
## Implémentation du Gestionnaire de commande  
 Aide pour la signature est généralement déclenché par un \(caractère et rejeté par un\) caractères. Vous pouvez gérer ces séquences de touches en implémentant un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> afin qu’il déclenche une session d’assistance de Signature lorsqu’elle reçoit un \(caractère précédé par un nom de méthode connue et ferme la session lorsqu’elle reçoit un\) caractères.  
  
#### Pour implémenter le Gestionnaire de commandes  
  
1.  Ajoutez une classe nommée `TestSignatureHelpCommand` qui implémente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!CODE [VSSDKSignatureHelpTest#24](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#24)]  
  
2.  Ajouter des champs privés pour le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptateur \(qui vous permet d’ajouter le Gestionnaire de commandes pour les gestionnaires de commandement\), l’affichage de texte, le broker d’assistance de Signature et une session, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, et l’autre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!CODE [VSSDKSignatureHelpTest#25](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#25)]  
  
3.  Ajoutez un constructeur pour initialiser ces champs et ajouter le filtre de commande pour les filtres de la chaîne de commande.  
  
     [!CODE [VSSDKSignatureHelpTest#26](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#26)]  
  
4.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> méthode pour déclencher la session d’assistance de Signature lorsque le filtre de commande reçoit un \(caractère après l’un des noms de méthode connue et pour fermer la session lorsqu’elle reçoit un\) caractères pendant que la session est toujours active. Dans tous les cas, la commande est transmise.  
  
     [!CODE [VSSDKSignatureHelpTest#27](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#27)]  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode afin qu’il transmet toujours la commande.  
  
     [!CODE [VSSDKSignatureHelpTest#28](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#28)]  
  
## Implémentation d’un fournisseur commande Help Signature  
 Vous pouvez fournir la commande Help Signature en implémentant le <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> pour instancier le Gestionnaire de commandes lors de l’affichage de texte est créé.  
  
#### Pour implémenter le fournisseur d’assistance de Signature commande  
  
1.  Ajoutez une classe nommée `TestSignatureHelpController` qui implémente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> et l’exporter avec la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, et <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!CODE [VSSDKSignatureHelpTest#29](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#29)]  
  
2.  Importer le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(permettant d’obtenir le <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, étant donné la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet\), la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> \(utilisé pour rechercher le mot en cours\) et le <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> \(pour déclencher la session d’assistance de Signature\).  
  
     [!CODE [VSSDKSignatureHelpTest#30](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#30)]  
  
3.  Implémentez la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> méthode en instanciant le `TestSignatureCommandHandler`.  
  
     [!CODE [VSSDKSignatureHelpTest#31](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#31)]  
  
## Création et test du code  
 Pour tester ce code, générez la solution SignatureHelpTest et exécutez\-le dans l’instance expérimentale.  
  
#### Pour générer et tester la solution SignatureHelpTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créez un fichier texte et du texte qui inclut le mot « ajouter » de type et une parenthèse ouvrante.  
  
4.  Une fois que vous tapez la parenthèse ouvrante, vous devez voir une info\-bulle qui affiche une liste des deux signatures pour le `add()` \(méthode\).  
  
## Voir aussi  
 [Procédure pas à pas : Liaison d'un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)