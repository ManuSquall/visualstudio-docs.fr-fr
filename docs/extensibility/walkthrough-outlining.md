---
title: "Proc&#233;dure pas &#224; pas : mise en relief | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - mode plan"
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Proc&#233;dure pas &#224; pas : mise en relief
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez implémenter en langage de fonctionnalités telles que le mode plan en définissant les types de zones de texte que vous souhaitez développer ou réduire. Vous pouvez définir des régions dans le contexte d'un service de langage, ou vous pouvez définir votre propre type de contenu et d'extension de nom fichier et appliquer la définition d'une région uniquement à ce type, ou vous pouvez appliquer les définitions de zone à un type de contenu existant \(par exemple, « texte »\). Cette procédure pas à pas montre comment définir et afficher les régions en mode plan.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’un projet Managed Extensibility Framework \(MEF\)  
  
#### Pour créer un projet MEF  
  
1.  Créez un projet VSIX. Nommez la solution `OutlineRegionTest`.  
  
2.  Ajouter un modèle d'élément éditeur classifieur au projet. Pour plus d'informations, consultez [Création d'une Extension avec un éditeur de modèle d'élément](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Supprimez les fichiers de classe existants.  
  
## L'implémentation d'une balise de mode plan  
 Régions en mode plan sont marquées par un type de balise \(<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>\). Cette balise fournit la norme mise en relief de comportement. La région de plan peut être développée ou réduite. La région de plan est marquée par un signe PLUS si elle est réduite ou un signe moins si elle est développée, et la région de développé est délimitée par une ligne verticale.  
  
 Les étapes suivantes montrent comment définir une balise qui crée des régions en mode plan pour toutes les régions qui sont délimitées par des « \[» et «\] ».  
  
#### Pour implémenter une balise en mode plan  
  
1.  Ajoutez un fichier de classe et nommez\-le `OutliningTagger`.  
  
2.  Importez les espaces de noms suivant.  
  
     [!code-cs[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Créez une classe nommée `OutliningTagger`, et qu'elle implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-cs[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Ajouter des champs pour effectuer le suivi de la mémoire tampon de texte et l'instantané et accumuler les ensembles de lignes qui doivent être marqués comme régions en mode plan. Ce code inclut une liste d'objets de zone \(pour être défini ultérieurement\) qui représentent les régions en mode plan.  
  
     [!code-cs[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Ajoutez un constructeur de balise qui initialise les champs, analyse de la mémoire tampon, et ajoute un gestionnaire d'événements pour le <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.  
  
     [!code-cs[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implémentez le <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> s'étend de méthode qui instancie la balise. Cet exemple suppose que les étendues dans le <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passé à la méthode sont contiguës, bien que cela puisse pas toujours le cas. Cette méthode instancie une nouvelle étendue de balise pour chacune des régions en mode plan.  
  
     [!code-cs[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Déclarez un `TagsChanged` Gestionnaire d'événements.  
  
     [!code-cs[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Ajouter un `BufferChanged` Gestionnaire d'événements qui répond aux <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événements par l'analyse de la mémoire tampon de texte.  
  
     [!code-cs[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Ajoutez une méthode qui analyse la mémoire tampon. L'exemple fourni ici est à titre d'illustration uniquement. Il analyse simultanément la mémoire tampon dans les régions en mode plan imbriquées.  
  
     [!code-cs[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. La méthode d'assistance suivante obtient un entier qui représente le niveau de la fonctionnalité mode plan, telles que 1 est la paire d'accolades à l'extrême gauche.  
  
     [!code-cs[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. La méthode d'assistance suivante traduit un SnapshotSpan une région \(définie plus loin dans cette rubrique\).  
  
     [!code-cs[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Le code suivant est à titre d'illustration uniquement. Il définit une classe PartialRegion qui contient le numéro de ligne et l'offset du début d'une région en mode plan et également une référence à la zone parent \(le cas échéant\). Ainsi, l'Analyseur de configuration imbriqués régions en mode plan. Une classe dérivée de la zone contient une référence au numéro de ligne de la fin d'une région en mode plan.  
  
     [!code-cs[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## Implémentation d'un fournisseur de balise  
 Vous devez exporter un fournisseur de balise pour votre balise. Le fournisseur de balise crée un `OutliningTagger` pour une mémoire tampon du type de contenu « texte », ou autre retourne un `OutliningTagger` Si la mémoire tampon en comporte déjà un.  
  
#### Pour implémenter un fournisseur de balise  
  
1.  Créez une classe nommée `OutliningTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, et exportez\-le avec les attributs ContentType et TagType.  
  
     [!code-cs[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en ajoutant un `OutliningTagger` aux propriétés de la mémoire tampon.  
  
     [!code-cs[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## Création et test du code  
 Pour tester ce code, générez la solution OutlineRegionTest et exécutez\-le dans l'instance expérimentale.  
  
#### Pour générer et tester la solution OutlineRegionTest  
  
1.  Générez la solution.  
  
2.  Lorsque vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est instanciée.  
  
3.  Créer un fichier texte. Tapez du texte qui inclut l'accolade ouvrante et l'accolade fermante.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Il doit exister une région en mode plan qui inclut les deux accolades. Vous serez sur le signe moins à gauche de l'accolade ouvrante pour réduire la région en mode plan. Lorsque la région est réduite, le symbole des points de suspension \(...\) doit apparaître à gauche de la région réduite et une fenêtre contextuelle contenant le texte **texte de pointage** doit s'afficher lorsque vous déplacez le pointeur sur le bouton de sélection.  
  
## Voir aussi  
 [Procédure pas à pas : Liaison d'un Type de contenu à une Extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)