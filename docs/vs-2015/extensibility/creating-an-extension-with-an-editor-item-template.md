---
title: Création d’une Extension avec un éditeur de modèle d’élément | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 245963c433c264212096d129d99d86367e006b4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501394"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Création d’une extension avec un modèle d’élément d’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [création d’une Extension avec un éditeur de modèle d’élément](https://docs.microsoft.com/visualstudio/extensibility/creating-an-extension-with-an-editor-item-template).  
  
Vous pouvez utiliser des modèles d’éléments qui sont inclus dans le SDK de Visual Studio pour créer des extensions de l’éditeur de base qui ajoutent des classifieurs, les ornements et les marges pour l’éditeur. Les modèles d’élément de l’éditeur sont disponibles pour les projets Visual c# ou Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Création d’une Extension de classifieur  
 Le modèle d’élément de classifieur d’éditeur crée un classifieur d’éditeur qui le colore le texte approprié (dans ce cas, tous les éléments) dans n’importe quel fichier texte.  
  
1.  Dans le **nouveau projet** boîte de dialogue, développez **Visual C#** ou **Visual Basic** puis cliquez sur **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans la zone **Nom**, tapez `TestClassifier`. Cliquez sur **OK**.  
  
2.  Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Accédez à Visual c# **extensibilité** nœud et sélectionnez **classifieur d’éditeur**. Laissez le nom de fichier par défaut (EditorClassifier1.cs).  
  
3.  Il existe trois fichiers de code, comme suit :  
  
    -   EditorClassifier1.cs contient la `EditorClassifier1` classe.  
  
    -   EditorClassifier1ClassificationDefinition.cs contient la `OEditorClassifier1ClassificationDefinition` classe.  
  
    -   EditorClassifier1Format.cs contient la `EditorClassifier1Format` classe.  
  
    -   EditorClassifier1Provider.cs contient la `EditorClassifier1Provider` classe.  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.  
  
     Si vous ouvrez un fichier texte, tout le texte est souligné par rapport à un arrière-plan violet.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Création d’une Extension de l’ornement de texte relatif  
 Le modèle de l’ornement de texte de l’éditeur crée un ornement de texte relative qui décore toutes les instances du caractère de texte « a » à l’aide d’une zone qui a un contour rouge et un arrière-plan bleu. Il est relatif de texte, car la zone toujours superpositions les caractères 'a', même lorsqu’ils sont déplacés ou remis en forme.  
  
1.  Dans le **nouveau projet** boîte de dialogue, développez **Visual C#** ou **Visual Basic** puis cliquez sur **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans la zone **Nom**, tapez `TestAdornment`. Cliquez sur **OK**.  
  
2.  Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Accédez à Visual c# **extensibilité** nœud et sélectionnez **ornement de texte éditeur**. Laissez le nom de fichier par défaut (TextAdornment1.cs/vb).  
  
3.  Il existe deux fichiers de code, comme suit :  
  
    -   TextAdornment1.cs contient la `TextAdornment1` classe.  
  
    -   extAdornment1TextViewCreationListener.cs contient la `TextAdornment1TextViewCreationListener` classe.  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche. Si vous ouvrez un fichier texte, « a » caractères dans le texte sont surlignées en rouge sur un arrière-plan bleu.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Création d’une Extension de l’ornement de la fenêtre d’affichage relatif  
 Le modèle de l’ornement de la fenêtre d’affichage de l’éditeur crée un ornement relatif à la fenêtre d’affichage qui ajoute une zone violette qui a un contour rouge à l’angle supérieur droit de la fenêtre d’affichage.  
  
> [!NOTE]
>  Le *viewport* est la zone de l’affichage de texte qui est actuellement affiché.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Pour créer une extension d’ornement de la fenêtre d’affichage en utilisant le modèle de l’ornement de la fenêtre d’affichage de l’éditeur  
  
1.  Dans le **nouveau projet** boîte de dialogue, développez **Visual C#** ou **Visual Basic** puis cliquez sur **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans la zone **Nom**, tapez `ViewportAdornment`. Cliquez sur **OK**.  
  
2.  Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Accédez à Visual c# **extensibilité** nœud et sélectionnez **ornement de la fenêtre d’affichage d’éditeur**. Laissez le nom de fichier par défaut (ViewportAdornment1.cs/vb).  
  
3.  Il existe deux fichiers de code, comme suit :  
  
    -   ViewportAdornment1.cs contient la `ViewportAdornment1` classe.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contient la `ViewportAdornment1TextViewCreationListener` classe  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche. Si vous créez un nouveau fichier texte, une zone violette comportant un contour rouge s’affiche dans l’angle supérieur droit de la fenêtre d’affichage.  
  
## <a name="creating-a-margin-extension"></a>Création d’une Extension de marge  
 Le modèle de la marge de l’éditeur crée une marge verte s’affiche avec les mots « Hello world ! » sous la barre de défilement horizontale.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Pour créer une extension de la marge en utilisant le modèle de la marge de l’éditeur  
  
1.  Dans le **nouveau projet** boîte de dialogue, développez **Visual C#** ou **Visual Basic** puis cliquez sur **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans la zone **Nom**, tapez `MarginExtension`. Cliquez sur **OK**.  
  
2.  Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Accédez à Visual c# **extensibilité** nœud et sélectionnez **ornement de la fenêtre d’affichage d’éditeur**. Laissez le nom de fichier par défaut (EditorMargin1.cs/vb).  
  
3.  Il existe deux fichiers de code, comme suit :  
  
    -   EditorMargin1.cs contient la `EditorMargin1` classe.  
  
    -   EditorMargin1Factory.cs contient la `EditorMargin1Factory` classe.  
  
4.  Générez ce projet et démarrer le débogage. L’instance expérimentale s’affiche. Si vous ouvrez un fichier texte, une marge vert qui a les mots « Hello EditorMargin1 » s’affiche sous la barre de défilement horizontale.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)

