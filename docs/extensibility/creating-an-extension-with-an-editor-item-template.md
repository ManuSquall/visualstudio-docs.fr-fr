---
title: "Cr&#233;ation d&#39;une Extension avec un &#233;diteur de mod&#232;le d&#39;&#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), nouvelles - extensions"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Cr&#233;ation d&#39;une Extension avec un &#233;diteur de mod&#232;le d&#39;&#233;l&#233;ment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser des modèles d'éléments qui sont inclus dans le SDK de Visual Studio pour créer des extensions d'éditeur de base qui ajoutent des classifieurs, motifs et les marges pour l'éditeur. Les modèles d'élément éditeur sont disponibles pour les projets Visual c\# ou Visual Basic VSIX.  
  
## Conditions préalables  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d'une Extension de classifieur  
 Le modèle d'élément éditeur classifieur crée un classifieur d'éditeur qui colore le texte approprié \(dans ce cas, tous les éléments\) dans un fichier texte.  
  
1.  Dans le **Nouveau projet** boîte de dialogue, développez **Visual C\#** ou **Visual Basic** puis **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans le **nom** tapez `TestClassifier`. Cliquez sur **OK**.  
  
2.  Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Accédez à Visual c\# **extensibilité** nœud et sélectionnez **éditeur classifieur**. Laissez le nom de fichier par défaut \(EditorClassifier1.cs\).  
  
3.  Il existe trois fichiers de code, comme suit :  
  
    -   EditorClassifier1.cs contient la `EditorClassifier1` classe.  
  
    -   EditorClassifier1ClassificationDefinition.cs contient la `OEditorClassifier1ClassificationDefinition` classe.  
  
    -   EditorClassifier1Format.cs contient la `EditorClassifier1Format`  classe.  
  
    -   EditorClassifier1Provider.cs contient la `EditorClassifier1Provider` classe.  
  
4.  Générez le projet et commencez le débogage. L'instance expérimentale de Visual Studio s'affiche.  
  
     Si vous ouvrez un fichier texte, tout le texte est souligné par rapport à un arrière\-plan violet.  
  
## Création d'une Extension de l'ornement de texte relatif  
 Le modèle de l'ornement de texte de l'éditeur crée un ornement de texte relatif qui décore toutes les instances du caractère de texte « a » à l'aide d'une zone avec un contour rouge et un arrière\-plan bleu. Il est relatif à texte, car la zone toujours superpositions les caractères 'a', même lorsqu'ils sont déplacés ou reformatés.  
  
1.  Dans le **Nouveau projet** boîte de dialogue, développez **Visual C\#** ou **Visual Basic** puis **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans le **nom** tapez `TestAdornment`. Cliquez sur **OK**.  
  
2.  Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Accédez à Visual c\# **extensibilité** nœud et sélectionnez **ornement de texte de l'éditeur**. Laissez le nom de fichier par défaut \(TextAdornment1.cs\/vb\).  
  
3.  Il existe deux fichiers de code, comme suit :  
  
    -   TextAdornment1.cs contient la `TextAdornment1` classe.  
  
    -   extAdornment1TextViewCreationListener.cs contient la `TextAdornment1TextViewCreationListener` classe.  
  
4.  Générez le projet et commencez le débogage. L'instance expérimentale s'affiche. Si vous ouvrez un fichier texte, « a » caractères dans le texte sont indiqués en rouge sur fond bleu.  
  
## Création d'une Extension de l'ornement de relatifs à la fenêtre d'affichage  
 Le modèle de l'ornement de la fenêtre d'affichage de l'éditeur crée un ornement relatif à la fenêtre d'affichage qui ajoute une zone violette avec un contour rouge vers le coin supérieur droit de la fenêtre d'affichage.  
  
> [!NOTE]
>  Le *viewport* est la zone de l'affichage de texte qui est actuellement affichée.  
  
#### Pour créer une extension d'ornement de la fenêtre d'affichage en utilisant le modèle d'ornement de la fenêtre d'affichage de l'éditeur  
  
1.  Dans le **Nouveau projet** boîte de dialogue, développez **Visual C\#** ou **Visual Basic** puis **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans le **nom** tapez `ViewportAdornment`. Cliquez sur **OK**.  
  
2.  Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Accédez à Visual c\# **extensibilité** nœud et sélectionnez **ornement de la fenêtre d'affichage de l'éditeur**. Laissez le nom de fichier par défaut \(ViewportAdornment1.cs\/vb\).  
  
3.  Il existe deux fichiers de code, comme suit :  
  
    -   ViewportAdornment1.cs contient la `ViewportAdornment1` classe.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contient le `ViewportAdornment1TextViewCreationListener` \(classe\)  
  
4.  Générez le projet et commencez le débogage. L'instance expérimentale s'affiche. Si vous créez un nouveau fichier texte, une zone violette avec un contour rouge s'affiche dans le coin supérieur droit de la fenêtre d'affichage.  
  
## Création d'une Extension de marge  
 Le modèle de la marge de l'éditeur crée une marge verte qui s'affiche avec les mots « Hello world\! » sous la barre de défilement horizontale.  
  
#### Pour créer une extension de marge à l'aide du modèle de la marge de l'éditeur  
  
1.  Dans le **Nouveau projet** boîte de dialogue, développez **Visual C\#** ou **Visual Basic** puis **extensibilité**. Dans le **modèles** volet, sélectionnez **projet VSIX**. Dans le **nom** tapez `MarginExtension`. Cliquez sur **OK**.  
  
2.  Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Accédez à Visual c\# **extensibilité** nœud et sélectionnez **ornement de la fenêtre d'affichage de l'éditeur**. Laissez le nom de fichier par défaut \(EditorMargin1.cs\/vb\).  
  
3.  Il existe deux fichiers de code, comme suit :  
  
    -   EditorMargin1.cs contient la `EditorMargin1` classe.  
  
    -   EditorMargin1Factory.cs contient la `EditorMargin1Factory` classe.  
  
4.  Générez ce projet et démarrer le débogage. L'instance expérimentale s'affiche. Si vous ouvrez un fichier texte, une marge verte qui comporte le mot « Bonjour EditorMargin1 » s'affiche sous la barre de défilement horizontale.  
  
## Voir aussi  
 [Service de langage et les Points d’Extension Éditeur](../extensibility/language-service-and-editor-extension-points.md)