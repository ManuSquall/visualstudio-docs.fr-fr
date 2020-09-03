---
title: 'Procédure pas à pas : mode plan | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201956"
---
# <a name="walkthrough-outlining"></a>Procédure pas à pas : mode Plan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez implémenter des fonctionnalités basées sur le langage, telles que le mode plan, en définissant les genres de zones de texte que vous souhaitez développer ou réduire. Vous pouvez définir des régions dans le contexte d’un service de langage, ou vous pouvez définir votre propre extension de nom de fichier et type de contenu et appliquer la définition de région uniquement à ce type, ou vous pouvez appliquer les définitions de zone à un type de contenu existant (tel que « texte »). Cette procédure pas à pas montre comment définir et afficher des régions en mode plan.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1. Créez un projet VSIX. Nommez la solution `OutlineRegionTest`.  
  
2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Supprimez les fichiers de classe existants.  
  
## <a name="implementing-an-outlining-tagger"></a>Implémentation d’une balise en mode plan  
 Les régions en mode plan sont marquées par un type de balise ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Cette balise fournit le comportement de mode plan standard. La zone en mode plan peut être développée ou réduite. La zone en mode plan est marquée par un signe PLUS si elle est réduite ou un signe moins si elle est développée, et la région développée est délimitée par une ligne verticale.  
  
 Les étapes suivantes montrent comment définir une balise qui crée des régions en mode plan pour toutes les régions délimitées par « [ » et « ] ».  
  
#### <a name="to-implement-an-outlining-tagger"></a>Pour implémenter une balise de mode plan  
  
1. Ajoutez un fichier de classe et nommez-le `OutliningTagger`.  
  
2. Importez les espaces de noms suivants.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Créez une classe nommée `OutliningTagger` et mettez-la en œuvre <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Ajoutez des champs pour effectuer le suivi de la mémoire tampon de texte et de l’instantané, et pour accumuler les ensembles de lignes qui doivent être balisés en tant que régions en mode plan. Ce code comprend une liste d’objets Region (à définir ultérieurement) qui représentent les régions en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Ajoutez un constructeur de balises qui initialise les champs, analyse la mémoire tampon et ajoute un gestionnaire d’événements à l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode, qui instancie les étendues de balise. Cet exemple suppose que les étendues dans le <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passé à la méthode sont contiguës, bien que cela ne soit pas toujours le cas. Cette méthode instancie une nouvelle étendue de balise pour chacune des régions en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Déclarez un `TagsChanged` Gestionnaire d’événements.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Ajoutez un `BufferChanged` Gestionnaire d’événements qui répond aux <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événements en analysant la mémoire tampon de texte.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Ajoutez une méthode qui analyse la mémoire tampon. L’exemple donné ici est fourni à titre d’illustration uniquement. Il analyse de façon synchrone la mémoire tampon dans des régions en mode plan imbriquées.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. La méthode d’assistance suivante obtient un entier qui représente le niveau du mode plan, de sorte que 1 est la paire d’accolades la plus à gauche.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. La méthode d’assistance suivante traduit une région (définie plus loin dans cette rubrique) en SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Le code suivant est uniquement à titre d’illustration. Il définit une classe PartialRegion qui contient le numéro de ligne et le décalage du début d’une région en mode plan, ainsi qu’une référence à la région parente (le cas échéant). Cela permet à l’analyseur de configurer des régions en mode plan imbriquées. Une classe de région dérivée contient une référence au numéro de ligne de la fin d’une région en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implémentation d’un fournisseur de balises  
 Vous devez exporter un fournisseur de balises pour votre balise. Le fournisseur de balises crée un `OutliningTagger` pour une mémoire tampon du type de contenu « text », ou sinon retourne un `OutliningTagger` si la mémoire tampon en a déjà un.  
  
#### <a name="to-implement-a-tagger-provider"></a>Pour implémenter un fournisseur de balises  
  
1. Créez une classe nommée `OutliningTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> et exportez-la avec les attributs ContentType et TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en ajoutant un `OutliningTagger` aux propriétés de la mémoire tampon.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution OutlineRegionTest et exécutez-la dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Pour générer et tester la solution OutlineRegionTest  
  
1. Générez la solution.  
  
2. Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3. Créer un fichier texte. Tapez du texte qui comprend à la fois l’accolade ouvrante et l’accolade fermante.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Il doit y avoir une région en mode plan qui inclut les deux accolades. Vous devez être en mesure de cliquer sur le signe moins à gauche de l’accolade ouvrante pour réduire la région en mode plan. Lorsque la région est réduite, le symbole des points de suspension (...) doit apparaître à gauche de la zone réduite et une fenêtre contextuelle contenant le **texte de pointage** s’affiche lorsque vous déplacez le pointeur sur les points de suspension.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
