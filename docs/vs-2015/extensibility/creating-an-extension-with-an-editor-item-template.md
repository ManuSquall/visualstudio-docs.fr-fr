---
title: Création d’une extension avec un modèle d’élément d’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840179"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Création d’une extension avec un modèle d’élément d’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser les modèles d’élément inclus dans le kit de développement logiciel (SDK) Visual Studio pour créer des extensions d’éditeur de base qui ajoutent des classifieurs, des ornements et des marges à l’éditeur. Les modèles d’élément de l’éditeur sont disponibles pour les projets Visual C# ou VSIX Visual Basic.  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Création d’une extension classifieur  
 Le modèle d’élément de classifieur d’éditeur crée un classifieur d’éditeur qui colore le texte approprié (dans ce cas, tout) dans un fichier texte.  
  
1. Dans la boîte de dialogue **nouveau projet** , développez **Visual C#** ou **Visual Basic** , puis cliquez sur **extensibilité**. Dans le volet **modèles** , sélectionnez **projet VSIX**. Dans le champ **Nom**, saisissez `TestClassifier`. Cliquez sur **OK**.  
  
2. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Accédez au nœud **extensibilité** Visual C# et sélectionnez **classifieur**de l’éditeur. Laissez le nom de fichier par défaut (EditorClassifier1.cs).  
  
3. Il existe trois fichiers de code, comme suit :  
  
    - EditorClassifier1.cs contient la `EditorClassifier1` classe.  
  
    - EditorClassifier1ClassificationDefinition.cs contient la `OEditorClassifier1ClassificationDefinition` classe.  
  
    - EditorClassifier1Format.cs contient la `EditorClassifier1Format`  classe.  
  
    - EditorClassifier1Provider.cs contient la `EditorClassifier1Provider` classe.  
  
4. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.  
  
     Si vous ouvrez un fichier texte, tout le texte est souligné par rapport à un arrière-plan violet.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Création d’une extension d’ornement relative à du texte  
 Le modèle d’ornement de texte de l’éditeur crée un ornement relatif au texte qui décore toutes les instances du caractère de texte « a » à l’aide d’une zone avec un contour rouge et un arrière-plan bleu. Elle est relative au texte, car la zone recouvre toujours les caractères « a », même lorsqu’ils sont déplacés ou reformatés.  
  
1. Dans la boîte de dialogue **nouveau projet** , développez **Visual C#** ou **Visual Basic** , puis cliquez sur **extensibilité**. Dans le volet **modèles** , sélectionnez **projet VSIX**. Dans le champ **Nom**, saisissez `TestAdornment`. Cliquez sur **OK**.  
  
2. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Accédez au nœud **extensibilité** Visual C# et sélectionnez l' **ornement de texte**de l’éditeur. Laissez le nom de fichier par défaut (TextAdornment1.cs/vb).  
  
3. Il existe deux fichiers de code, comme suit :  
  
    - TextAdornment1.cs contient la `TextAdornment1` classe.  
  
    - extAdornment1TextViewCreationListener.cs contient la `TextAdornment1TextViewCreationListener` classe.  
  
4. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche. Si vous ouvrez un fichier texte, tous les caractères « a » dans le texte sont soulignés en rouge sur un arrière-plan bleu.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Création d’une extension d’ornement relative à Viewport  
 Le modèle d’ornement de fenêtre d’affichage de l’éditeur crée un ornement relatif à la fenêtre d’affichage qui ajoute une zone violette avec un contour rouge dans le coin supérieur droit de la fenêtre d’affichage.  
  
> [!NOTE]
> La *fenêtre* d’affichage est la zone de la vue de texte actuellement affichée.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Pour créer une extension d’ornement de fenêtre d’affichage à l’aide du modèle d’ornement Viewport de l’éditeur  
  
1. Dans la boîte de dialogue **nouveau projet** , développez **Visual C#** ou **Visual Basic** , puis cliquez sur **extensibilité**. Dans le volet **modèles** , sélectionnez **projet VSIX**. Dans le champ **Nom**, saisissez `ViewportAdornment`. Cliquez sur **OK**.  
  
2. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Accédez au nœud **extensibilité** Visual C# et sélectionnez l' **ornement**de la fenêtre d’affichage de l’éditeur. Laissez le nom de fichier par défaut (ViewportAdornment1.cs/vb).  
  
3. Il existe deux fichiers de code, comme suit :  
  
    - ViewportAdornment1.cs contient la `ViewportAdornment1` classe.  
  
    - ViewportAdornment1TextViewCreationListener.cs contient la `ViewportAdornment1TextViewCreationListener` classe  
  
4. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche. Si vous créez un nouveau fichier texte, une zone violette avec un contour rouge s’affiche dans l’angle supérieur droit de la fenêtre d’affichage.  
  
## <a name="creating-a-margin-extension"></a>Création d’une extension de marge  
 Le modèle de marge de l’éditeur crée une marge verte qui s’affiche avec les mots « Hello World ! » sous la barre de défilement horizontale.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Pour créer une extension de marge à l’aide du modèle de marge de l’éditeur  
  
1. Dans la boîte de dialogue **nouveau projet** , développez **Visual C#** ou **Visual Basic** , puis cliquez sur **extensibilité**. Dans le volet **modèles** , sélectionnez **projet VSIX**. Dans le champ **Nom**, saisissez `MarginExtension`. Cliquez sur **OK**.  
  
2. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Accédez au nœud **extensibilité** Visual C# et sélectionnez l' **ornement**de la fenêtre d’affichage de l’éditeur. Laissez le nom de fichier par défaut (EditorMargin1.cs/vb).  
  
3. Il existe deux fichiers de code, comme suit :  
  
    - EditorMargin1.cs contient la `EditorMargin1` classe.  
  
    - EditorMargin1Factory.cs contient la `EditorMargin1Factory` classe.  
  
4. Générez ce projet et démarrez le débogage. L’instance expérimentale s’affiche. Si vous ouvrez un fichier texte, une marge verte contenant les mots « Hello EditorMargin1 » s’affiche sous la barre de défilement horizontale.  
  
## <a name="see-also"></a>Voir aussi  
 [Points d’extension du service de langage et de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
