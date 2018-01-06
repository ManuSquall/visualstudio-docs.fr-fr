---
title: "Procédure pas à pas : Mise en relief | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15dd5f0121fca86a38631bf775ec25d4428632e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-outlining"></a>Procédure pas à pas : mise en relief
Vous pouvez implémenter basée sur le langage des fonctionnalités telles que le mode plan en définissant les types de zones de texte que vous souhaitez développer ou réduire. Vous pouvez définir des régions dans le contexte d’un service de langage, ou vous pouvez définir votre propre type de contenu et d’extension de nom du fichier et appliquer la définition de la région uniquement à ce type, ou vous pouvez appliquer les définitions de zone à un type de contenu existant (par exemple « text »). Cette procédure pas à pas montre comment définir et afficher les régions en mode plan.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Création d’un projet Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF  
  
1.  Créez un projet VSIX. Nommez la solution `OutlineRegionTest`.  
  
2.  Ajouter un modèle d’élément classifieur d’éditeur pour le projet. Pour plus d’informations, consultez [création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## <a name="implementing-an-outlining-tagger"></a>Implémentation d’un Baliseur en mode plan  
 Régions en mode plan sont marquées par un type de balise (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Cette balise fournit la norme de comportement de mise en relief. La région de plan peut être développée ou réduite. La région encadrée est marquée par un signe PLUS, si elle est réduite ou d’un signe moins si elle est développée, et la région de développé est délimitée par une ligne verticale.  
  
 Les étapes suivantes montrent comment définir une balise qui crée des régions en mode plan pour toutes les régions qui sont délimitées par « [ » et «] ».  
  
#### <a name="to-implement-an-outlining-tagger"></a>Pour implémenter un baliseur en mode plan  
  
1.  Ajoutez un fichier de classe et nommez-le `OutliningTagger`.  
  
2.  Importez les espaces de noms suivants.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Créez une classe nommée `OutliningTagger`, et qu’elle implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Ajouter des champs pour effectuer le suivi de la mémoire tampon de texte et l’instantané et accumuler les ensembles de lignes qui doivent être référencées comme régions en mode plan. Ce code inclut une liste d’objets de région (à définir ultérieurement) qui représentent les régions en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Ajoutez un constructeur de balise qui initialise les champs, analyse de la mémoire tampon, et ajoute un gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> s’étend de méthode qui instancie la balise. Cet exemple part du principe que les étendues dans le <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passé à la méthode sont contiguës, bien que cela ne peut pas être toujours le cas. Cette méthode instancie une nouvelle étendue de balise pour chacune des régions en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Déclarez un `TagsChanged` Gestionnaire d’événements.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Ajouter un `BufferChanged` Gestionnaire d’événements qui répond aux <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événements par l’analyse de la mémoire tampon de texte.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Ajoutez une méthode qui analyse la mémoire tampon. L’exemple indiqué ici est à titre d’illustration uniquement. Mode synchrone, il analyse la mémoire tampon dans les régions en mode plan imbriquées.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. La méthode d’assistance suivante obtient un entier qui représente le niveau de la fonctionnalité mode plan, tels que 1 est la paire d’accolades plus à gauche.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. La méthode d’assistance suivante traduit un SnapshotSpan une région (définie plus loin dans cette rubrique).  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Le code suivant est à titre d’illustration uniquement. Il définit une classe PartialRegion qui contient le numéro de ligne et le décalage du début d’une région en mode plan et également une référence à la zone parent (le cas échéant). Ainsi, l’Analyseur de configuration imbriqués régions en mode plan. Une classe dérivée de la zone contient une référence au numéro de ligne de la fin d’une région en mode plan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implémentation d’un fournisseur de Baliseur  
 Vous devez exporter un fournisseur de baliseur pour votre baliseur. Le fournisseur de baliseur crée un `OutliningTagger` pour une mémoire tampon du type de contenu « text » ou autre retourne un `OutliningTagger` si la mémoire tampon en comporte déjà un.  
  
#### <a name="to-implement-a-tagger-provider"></a>Pour implémenter un fournisseur de baliseur  
  
1.  Créez une classe nommée `OutliningTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>et l’exporter avec les attributs ContentType et TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en ajoutant un `OutliningTagger` aux propriétés de la mémoire tampon.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Création et test du code  
 Pour tester ce code, générez la solution OutlineRegionTest et l’exécuter dans l’instance expérimentale.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Pour générer et tester la solution OutlineRegionTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créer un fichier texte. Tapez du texte qui inclut l’accolade ouvrante et l’accolade fermante.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Il doit y avoir une région en mode plan qui inclut les deux accolades. Vous devez être en mesure de cliquer sur le signe moins à gauche de l’accolade ouvrante pour réduire la région en mode plan. Lorsque la région est réduit, le symbole de points de suspension (...) doit apparaître à gauche de la région réduite et une fenêtre contextuelle qui contient le texte **texte de pointage** doit apparaître lorsque vous déplacez le pointeur sur le bouton de sélection.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)