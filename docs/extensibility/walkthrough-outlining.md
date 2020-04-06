---
title: 'Procédure pas à pas : Décrivant Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697215"
---
# <a name="walkthrough-outlining"></a>Procédure pas à pas : mode Plan
Configurez des fonctionnalités basées sur la langue telles que la définition des types de régions textuelles que vous souhaitez élargir ou s’effondrer. Vous pouvez définir des régions dans le cadre d’un service linguistique, ou définir votre propre extension de nom de fichier et type de contenu et appliquer la définition de la région uniquement à ce type, ou appliquer les définitions de la région à un type de contenu existant (comme le « texte »). Ce pas-là montre comment définir et afficher les régions décrivantes.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Créer un projet de cadre d’exténuabilité gérée (MEF)

### <a name="to-create-a-mef-project"></a>Pour créer un projet MEF

1. Créez un projet VSIX. Nommez la solution `OutlineRegionTest`.

2. Ajoutez un modèle d’élément Classificateur d’éditeur au projet. Pour plus d’informations, voir [Créer une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Supprimez les fichiers de classe existants.

## <a name="implement-an-outlining-tagger"></a>Mettre en œuvre un tagger décrivant
 Les régions qui distinguent sont<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>marquées par une sorte d’étiquette (). Cette balise fournit le comportement standard décrivant. La région décrite peut être élargie ou effondrée. La région décrite est marquée par**+** un signe Plus ( )**-** si elle s’est effondrée ou un signe Minus ( ) si elle est élargie, et la région élargie est délimitée par une ligne verticale.

 Les étapes suivantes montrent comment définir un tagger qui crée des régions décrivantes pour toutes les régions délimitées par les parenthèses (**[****, ]**).

### <a name="to-implement-an-outlining-tagger"></a>Mettre en œuvre un tagger décrivant

1. Ajoutez un fichier de classe et nommez-le `OutliningTagger`.

2. Importez les espaces nom suivants.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Créez une `OutliningTagger`classe nommée , <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>et faites-la implémenter :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Ajoutez quelques champs pour suivre le tampon de texte et l’instantané et pour accumuler les ensembles de lignes qui doivent être étiquetés comme des régions décrivantes. Ce code comprend une liste d’objets régionaux (à définir plus tard) qui représentent les régions encles.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Ajoutez un constructeur de tagger qui initialise les champs, analyse le tampon <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> et ajoute un gestionnaire d’événements à l’événement.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implémenter la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> méthode, qui instantanément les travées d’étiquette. Cet exemple suppose que les <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> travées dans le passage à la méthode sont contigus, bien qu’il ne soit pas toujours le cas. Cette méthode instantanément une nouvelle durée d’étiquette pour chacune des régions décrivant.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Déclarez `TagsChanged` un gestionnaire d’événements.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Ajoutez `BufferChanged` un gestionnaire d’événements qui répond aux <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> événements en analyseant le tampon de texte.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Ajoutez une méthode qui analyse le tampon. L’exemple donné ici est pour illustration seulement. Il analyse synchronisée le tampon en régions de grande réserve imbriquées.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. La méthode d’aide suivante obtient un intégrateur qui représente le niveau de la mise en évidence, de sorte que 1 est la paire d’accolade la plus gauche.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. La méthode d’assistance suivante traduit une région (définie plus tard dans cet article) en un SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Le code suivant est pour illustration seulement. Il définit une classe partiale qui contient le numéro de ligne et la compensation du début d’une région décrivante, et une référence à la région mère (le cas échéant). Ce code permet au parser de mettre en place des régions de mise en valeur imbriquées. Une classe de région dérivée contient une référence au numéro de ligne de la fin d’une région décrivante.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Mettre en œuvre un fournisseur de tagger
 Exportez un fournisseur de tagger pour votre tagger. Le fournisseur de `OutliningTagger` tagger crée un tampon pour un tampon `OutliningTagger` du type de contenu "texte", ou bien retourne un si le tampon a déjà un.

### <a name="to-implement-a-tagger-provider"></a>Mettre en œuvre un fournisseur de tagger

1. Créez une `OutliningTaggerProvider` classe nommée <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>qui implémente et exportez-la avec les attributs ContentType et TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implémenter <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> la `OutliningTagger` méthode en ajoutant un aux propriétés du tampon.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Construire et tester le code
 Pour tester ce code, créez la solution OutlineRegionTest et exécutez-la dans le cas expérimental.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Construire et tester la solution OutlineRegionTest

1. Générez la solution.

2. Lorsque vous exécutez ce projet dans le débbugger, une deuxième instance de Visual Studio est lancée.

3. Créer un fichier texte. Tapez un texte qui inclut à la fois les supports d’ouverture et les supports de fermeture.

    ```
    [
       Hello
    ]
    ```

4. Il devrait y avoir une région qui comprend les deux parenthèses. Vous devriez être en mesure de cliquer sur le signe Moins à gauche de la parenthèse ouverte pour effondrer la région de la ligne de délindation. Lorsque la région est effondrée, le symbole d’élipèse (*...*) devrait apparaître à gauche de la région effondrée, et un popup contenant le **texte planant** du texte devrait apparaître lorsque vous déplacez le pointeur sur l’ellipsis.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : liez un type de contenu à une extension de nom de fichier](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
