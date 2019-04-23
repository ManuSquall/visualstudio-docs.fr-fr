---
title: 'Procédure pas à pas : Mode Plan | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054702"
---
# <a name="walkthrough-outlining"></a>Procédure pas à pas : mode Plan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez implémenter des fonctionnalités reposant sur le langage comme le mode plan en définissant les types de zones de texte que vous souhaitez développer ou réduire. Vous pouvez définir des régions dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom fichier et s’appliquent de la définition de la région à uniquement à ce type, ou vous pouvez appliquer les définitions de la région à un type de contenu existant (par exemple, « text »). Cette procédure pas à pas montre comment définir et afficher les régions en mode plan.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1. Créez un projet VSIX. Nommez la solution `OutlineRegionTest`.  
  
2. Ajouter un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Supprimez les fichiers de classe existants.  
  
## <a name="implementing-an-outlining-tagger"></a>Implémentation d’une balise en mode plan  
 Régions en mode plan sont marquées par un type de balise (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Cette balise fournit la norme de comportement de mise en relief. La zone peut être développée ou réduite. La zone est marquée par un signe plus si elle est réduite ou d’un signe moins si elle est développée, et la région développée est délimitée par une ligne verticale.  
  
 Les étapes suivantes montrent comment définir une balise qui crée des régions en mode plan pour toutes les régions qui sont délimitées par « [ » et «] ».  
  
#### <a name="to-implement-an-outlining-tagger"></a>Pour implémenter une balise en mode plan  
  
1. Ajoutez un fichier de classe et nommez-le `OutliningTagger`.  
  
2. Importez les espaces de noms suivants.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Créez une classe nommée `OutliningTagger`, et qu’elle implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Ajouter des champs pour effectuer le suivi de la mémoire tampon de texte et l’instantané et accumuler les ensembles de lignes qui doivent être marqués comme régions en mode plan. Ce code inclut une liste d’objets de région (à définir ultérieurement) qui représentent les régions en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Ajoutez un constructeur de la balise qui initialise les champs, analyse de la mémoire tampon, et ajoute un gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implémentez le <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> s’étend de méthode qui instancie la balise. Cet exemple suppose que les étendues dans le <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passé à la méthode sont contiguës, bien que cela ne pouvez pas toujours le cas. Cette méthode instancie un nouvel intervalle de balise pour chacune des régions en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Déclarez un `TagsChanged` Gestionnaire d’événements.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Ajouter un `BufferChanged` Gestionnaire d’événements qui répond à <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événements en analysant la mémoire tampon de texte.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Ajoutez une méthode qui analyse la mémoire tampon. L’exemple fourni ici est à titre d’illustration uniquement. Mode synchrone, il analyse la mémoire tampon dans les régions en mode plan imbriquées.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. La méthode d’assistance suivante obtient un entier qui représente le niveau de la fonctionnalité mode plan, telles que 1 est la paire d’accolades à l’extrême gauche.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. La méthode d’assistance suivante traduit un SnapshotSpan une région (définie plus loin dans cette rubrique).  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Le code suivant est à titre d’illustration uniquement. Il définit une classe PartialRegion qui contient le numéro de ligne et l’offset du début d’une région en mode plan et également une référence à la zone parent (le cas échéant). Ainsi, l’Analyseur de configuration imbriqués régions en mode plan. Une classe dérivée de la région contient une référence au numéro de ligne de la fin d’une région en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implémentation d’un fournisseur de Baliseur  
 Vous devez exporter un fournisseur de baliseur pour votre balise. Le fournisseur de baliseur crée un `OutliningTagger` pour une mémoire tampon du type de contenu « texte », ou autre un `OutliningTagger` si la mémoire tampon en comporte déjà un.  
  
#### <a name="to-implement-a-tagger-provider"></a>Pour implémenter un fournisseur de baliseur  
  
1. Créez une classe nommée `OutliningTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>et exportez-le avec les attributs ContentType et TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implémentez le <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en ajoutant un `OutliningTagger` aux propriétés de la mémoire tampon.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution OutlineRegionTest et exécutez-le dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Pour générer et tester la solution OutlineRegionTest  
  
1. Générez la solution.  
  
2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3. Créer un fichier texte. Tapez du texte qui inclut l’accolade ouvrante et l’accolade fermante.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Il doit y avoir une région en mode plan qui inclut les deux accolades. Vous pourrez cliquer sur le signe moins à gauche de l’accolade ouvrante pour réduire la région en mode plan. Lorsque la région est réduite, le symbole de points de suspension (...) doit apparaître à gauche de la région réduite et une fenêtre contextuelle contenant le texte **texte de pointage** doit apparaître lorsque vous déplacez le pointeur sur le bouton de sélection.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
