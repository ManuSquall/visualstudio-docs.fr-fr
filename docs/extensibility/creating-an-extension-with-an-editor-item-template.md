---
title: Création d’une extension avec un modèle d’article de l’éditeur ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739502"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Créez une extension avec un modèle d’élément d’éditeur
Vous pouvez utiliser des modèles d’objets qui sont inclus dans le Visual Studio SDK pour créer des extensions d’éditeur de base qui ajoutent des classificateurs, des parures et des marges à l’éditeur. Les modèles d’articles de l’éditeur sont disponibles pour les projets VISUAL CMD ou Visual Basic VSIX.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Créer une extension de classificateur
 Le modèle d’élément Classificateur d’éditeur crée un classificateur d’éditeur qui colore le texte approprié (dans ce cas, tout) dans n’importe quel fichier texte.

1. Dans la boîte de dialogue **du nouveau projet,** élargissez **Visual C ou** Visual **Basic,** puis cliquez sur **Extensibility**. Dans la vitre **Templates,** sélectionnez **vsIX Project**. Dans le champ **Nom**, saisissez `TestClassifier`. Cliquez sur **OK**.

2. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Rendez-vous sur le nœud Visual **C’Extensibility** et sélectionnez **Le Classificateur d’éditeur.** Laissez le nom de fichier par défaut (*EditorClassifier1.cs*).

3. Il y a quatre fichiers de code, comme suit :

    - *EditorClassifier1.cs* contient la `EditorClassifier1` classe.

    - *EditorClassifier1ClassificationDefinition.cs* contient la `EditorClassifier1ClassificationDefinition` classe.

    - *EditorClassifier1Format.cs* contient la `EditorClassifier1Format` classe.

    - *EditorClassifier1Provider.cs* contient la `EditorClassifier1Provider` classe.

4. Générez le projet et commencez le débogage. L’exemple expérimental de Visual Studio apparaît.

     Si vous ouvrez un fichier texte, tout le texte est souligné sur fond violet.

## <a name="create-a-text-relative-adornment-extension"></a>Créer une extension d’ornement texte-relative
 Le modèle d’ornement de texte d’éditeur crée une parure textuelle relative qui décore tous les cas du caractère de texte 'a' en utilisant une boîte qui a un contour rouge et un fond bleu. Il est text-relatif parce que la boîte superpose toujours les caractères «a», même lorsqu’ils sont déplacés ou reformatés.

1. Dans la boîte de dialogue **du nouveau projet,** élargissez **Visual C ou** Visual **Basic,** puis cliquez sur **Extensibility**. Dans la vitre **Templates,** sélectionnez **vsIX Project**. Dans le champ **Nom**, saisissez `TestAdornment`. Cliquez sur **OK**.

2. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Rendez-vous sur le nœud Visual **C’Extensibility** et sélectionnez **Editor Text Adornment**. Laissez le nom de fichier par défaut (*TextAdornment1.cs/vb*).

3. Il existe deux fichiers de code, comme suit :

    - *TextAdornment1.cs* contient la `TextAdornment1` classe.

    - *TextAdornment1TextViewCreationListener.cs* contient la `TextAdornment1TextViewCreationListener` classe.

4. Générez le projet et commencez le débogage. L’instance expérimentale apparaît. Si vous ouvrez un fichier texte, tous les caractères «a» dans le texte sont décrits en rouge sur un fond bleu.

## <a name="create-a-viewport-relative-adornment-extension"></a>Créer une extension d’ornements viewport-relative
 Le modèle d’ornement Viewport de l’éditeur crée un ornement viewport-relatif qui ajoute une boîte violette qui a un contour rouge au coin supérieur droit du viewport.

> [!NOTE]
> Le **viewport** est la zone de l’affichage du texte qui est actuellement affichée.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Pour créer une extension de parure viewport en utilisant le modèle d’ornement Viewport Editor

1. Dans la boîte de dialogue **du nouveau projet,** élargissez **Visual C ou** Visual **Basic,** puis cliquez sur **Extensibility**. Dans la vitre **Templates,** sélectionnez **vsIX Project**. Dans le champ **Nom**, saisissez `ViewportAdornment`. Cliquez sur **OK**.

2. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Rendez-vous sur le nœud Visual **C’Extensibility** et sélectionnez **l’éditeur Viewport Adornment**. Laissez le nom de fichier par défaut (*ViewportAdornment1.cs/vb*).

3. Il existe deux fichiers de code, comme suit :

    - *ViewportAdornment1.cs* contient la `ViewportAdornment1` classe.

    - *ViewportAdornment1TextViewCreationListener.cs* contient la `ViewportAdornment1TextViewCreationListener` classe

4. Générez le projet et commencez le débogage. L’instance expérimentale apparaît. Si vous créez un nouveau fichier texte, une boîte violette qui a un contour rouge est affichée dans le coin supérieur droit du viewport.

## <a name="create-a-margin-extension"></a>Créer une extension de marge
 Le modèle de marge d’éditeur crée une marge verte qui apparaît avec les mots '*Bonjour monde!* au-dessous de la barre de défilement horizontal.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Pour créer une extension de marge en utilisant le modèle de marge de l’éditeur

1. Dans la boîte de dialogue **du nouveau projet,** élargissez **Visual C ou** Visual **Basic,** puis cliquez sur **Extensibility**. Dans la vitre **Templates,** sélectionnez **vsIX Project**. Dans le champ **Nom**, saisissez `MarginExtension`. Cliquez sur **OK**.

2. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Rendez-vous sur le nœud Visual **C’Extensibility** et sélectionnez **La marge de l’éditeur**. Laissez le nom du fichier par défaut (EditorMargin1.cs/vb).

3. Il existe deux fichiers de code, comme suit :

    - *EditorMargin1.cs* contient la `EditorMargin1` classe.

    - *EditorMargin1Factory.cs* contient la `EditorMargin1Factory` classe.

4. Construisez ce projet et commencez à débogage. L’instance expérimentale apparaît. Si vous ouvrez un fichier texte, une marge verte qui a les mots **Bonjour EditorMargin1** est affichée en dessous de la barre de défilement horizontal.

## <a name="see-also"></a>Voir aussi
- [Service linguistique et points d’extension de l’éditeur](../extensibility/language-service-and-editor-extension-points.md)
