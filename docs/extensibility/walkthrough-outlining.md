---
title: 'Procédure pas à pas : mode plan | Microsoft Docs'
description: Découvrez comment définir et afficher des régions en mode plan dans le contexte d’un service de langage ou pour votre propre extension de nom de fichier et type de contenu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7bf4c0cc8757ea4f034da2ac17d6c76971f86305
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217227"
---
# <a name="walkthrough-outlining"></a>Procédure pas à pas : mode Plan
Configurez des fonctionnalités basées sur le langage, telles que le mode plan, en définissant les genres de zones de texte que vous souhaitez développer ou réduire. Vous pouvez définir des régions dans le contexte d’un service de langage, ou définir votre propre extension de nom de fichier et type de contenu, appliquer la définition de région à ce type uniquement ou appliquer les définitions de régions à un type de contenu existant (tel que « texte »). Cette procédure pas à pas montre comment définir et afficher des régions en mode plan.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet VSIX. Nommez la solution `OutlineRegionTest`.

2. Ajoutez un modèle d’élément de classifieur d’éditeur au projet. Pour plus d’informations, consultez [créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-an-outlining-tagger"></a>Implémenter une balise de mode plan
 Les régions en mode plan sont marquées par un type de balise ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Cette balise fournit le comportement de mode plan standard. La zone en mode plan peut être développée ou réduite. La zone en mode plan est marquée par un signe plus ( **+** ) si elle est réduite ou un signe moins ( **-** ) si elle est développée, et la région développée est délimitée par une ligne verticale.

 Les étapes suivantes montrent comment définir une balise qui crée des régions en mode plan pour toutes les régions délimitées par des crochets (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Pour implémenter une balise de mode plan

1. Ajoutez un fichier de classe et nommez-le `OutliningTagger`.

2. Importez les espaces de noms suivants.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet1":::

3. Créez une classe nommée `OutliningTagger` et mettez-la en œuvre <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet2":::

4. Ajoutez des champs pour effectuer le suivi de la mémoire tampon de texte et de l’instantané, et pour accumuler les ensembles de lignes qui doivent être balisés en tant que régions en mode plan. Ce code comprend une liste d’objets Region (à définir ultérieurement) qui représentent les régions en mode plan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet3":::

5. Ajoutez un constructeur de balises qui initialise les champs, analyse la mémoire tampon et ajoute un gestionnaire d’événements à l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événement.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet4":::

6. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode, qui instancie les étendues de balise. Cet exemple suppose que les étendues dans le <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passé à la méthode sont contiguës, bien que cela ne soit pas toujours le cas. Cette méthode instancie une nouvelle étendue de balise pour chacune des régions en mode plan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet5":::

7. Déclarez un `TagsChanged` Gestionnaire d’événements.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet6":::

8. Ajoutez un `BufferChanged` Gestionnaire d’événements qui répond aux <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événements en analysant la mémoire tampon de texte.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet7":::

9. Ajoutez une méthode qui analyse la mémoire tampon. L’exemple donné ici est fourni à titre d’illustration uniquement. Il analyse de façon synchrone la mémoire tampon dans des régions en mode plan imbriquées.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet8":::

10. La méthode d’assistance suivante obtient un entier qui représente le niveau du mode plan, de sorte que 1 est la paire d’accolades la plus à gauche.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet9":::

11. La méthode d’assistance suivante traduit une région (définie plus loin dans cet article) en SnapshotSpan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet10":::

12. Le code suivant est uniquement à titre d’illustration. Il définit une classe PartialRegion qui contient le numéro de ligne et le décalage du début d’une région en mode plan, ainsi qu’une référence à la région parente (le cas échéant). Ce code permet à l’analyseur de configurer des régions en mode plan imbriquées. Une classe de région dérivée contient une référence au numéro de ligne de la fin d’une région en mode plan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet11":::

## <a name="implement-a-tagger-provider"></a>Implémenter un fournisseur de balises
 Exportez un fournisseur de balises pour votre balise. Le fournisseur de balises crée un `OutliningTagger` pour une mémoire tampon du type de contenu « text », ou sinon retourne un `OutliningTagger` si la mémoire tampon en a déjà un.

### <a name="to-implement-a-tagger-provider"></a>Pour implémenter un fournisseur de balises

1. Créez une classe nommée `OutliningTaggerProvider` qui implémente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> et exportez-la avec les attributs ContentType et TagType.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet12":::

2. Implémentez la <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> méthode en ajoutant un `OutliningTagger` aux propriétés de la mémoire tampon.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet13":::

## <a name="build-and-test-the-code"></a>Générer et tester le code
 Pour tester ce code, générez la solution OutlineRegionTest et exécutez-la dans l’instance expérimentale.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Pour générer et tester la solution OutlineRegionTest

1. Générez la solution.

2. Quand vous exécutez ce projet dans le débogueur, une deuxième instance de Visual Studio est démarrée.

3. Créer un fichier texte. Tapez du texte qui comprend à la fois les crochets ouvrants et les crochets fermants.

    ```
    [
       Hello
    ]
    ```

4. Il doit y avoir une région en mode plan qui inclut les deux crochets. Vous devez être en mesure de cliquer sur le signe moins à gauche du crochet ouvrant pour réduire la région en mode plan. Lorsque la région est réduite, le symbole des points de suspension (*...*) doit apparaître à gauche de la zone réduite et une fenêtre contextuelle contenant le **texte de pointage** s’affiche lorsque vous déplacez le pointeur sur les points de suspension.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liaison d’un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
