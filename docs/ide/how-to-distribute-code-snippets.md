---
title: Distribuer des extraits de code en tant qu’extension
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f0b3211352dc16e51b64196e13f7378bf2a423c
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355420"
---
# <a name="how-to-distribute-code-snippets"></a>Procédure : Distribuer des extraits de code

Vous pouvez donner des extraits de code à vos amis pour qu’ils les installent sur leurs ordinateurs à l’aide du **Gestionnaire des extraits de code**. Cependant, si vous avez plusieurs extraits de code à distribuer ou que vous voulez les distribuer à plus grande échelle, vous pouvez inclure vos fichiers d’extraits de code dans une extension Visual Studio. Les utilisateurs de Visual Studio peuvent ensuite installer l’extension pour obtenir les extraits de code.

## <a name="prerequisites"></a>Prérequis

Installez la charge de travail **Développement d’extension Visual Studio** pour accéder aux modèles de projet **Projet VSIX**.

![Charge de travail Développement d’extension Visual Studio](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Configurer l’extension

Dans cette procédure, vous utilisez l’extrait de code Hello World créé dans [Procédure pas à pas : Créer un extrait de code](../ide/walkthrough-creating-a-code-snippet.md). Cet article fournit l’extrait de code XML : vous n’êtes donc pas obligé de revenir en arrière et de créer un extrait de code.

1. Créez un projet à partir du modèle **Projet VSIX vide** et nommez le projet **TestSnippet**.

2. Dans le projet **TestSnippet**, ajoutez un nouveau fichier XML et appelez-le *VBCodeSnippet.snippet*. Remplacez le contenu par le code XML suivant :

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Configurer la structure des répertoires

1. Dans **Explorateur de solutions**, sélectionnez le nœud de projet et ajoutez un dossier portant le nom que vous souhaitez donner à l’extrait dans le **Gestionnaire des extraits de code**. Dans le cas présent, il doit s’agir de **HelloWorldVB**.

2. Déplacez le fichier *.snippet* vers le dossier *HelloWorldVB*.

3. Sélectionnez le fichier *.snippet* dans **Explorateur de solutions**. Dans la fenêtre **Propriétés**, vérifiez que **Action de génération** a la valeur **Contenu**, que **Copier dans le répertoire de sortie** a la valeur **Toujours copier** et que **Inclure dans VSIX** a la valeur **true**.

### <a name="add-the-pkgdef-file"></a>Ajouter le fichier .pkgdef

::: moniker range="vs-2017"

1. Ajoutez un fichier texte dans le dossier *HelloWorldVB* et nommez-le *HelloWorldVB.pkgdef*. Ce fichier permet d'ajouter certaines clés dans le Registre. Dans ce cas, il ajoute une nouvelle sous-clé à la clé **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ajoutez un fichier texte dans le dossier *HelloWorldVB* et nommez-le *HelloWorldVB.pkgdef*. Ce fichier permet d'ajouter certaines clés dans le Registre. Dans ce cas, il ajoute une nouvelle sous-clé à la clé **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic**.

::: moniker-end

2. Ajoutez les lignes ci-dessous au fichier.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Si vous examinez cette clé, vous pouvez voir comment spécifier des langues différentes.

3. Sélectionnez le fichier *.pkgdef* dans **l’Explorateur de solutions**, puis, dans la fenêtre **Propriétés**, assurez-vous que :

   - **Action de génération** a la valeur **Contenu**
   - **Copier dans le répertoire de sortie** a la valeur **Toujours copier**
   - **Inclure dans VSIX** a la valeur **true**

4. Ajoutez le fichier *.pkgdef* en tant que composant dans le manifeste VSIX. Dans le fichier *source.extension.vsixmanifest*, accédez à l’onglet **Ressources**, puis cliquez sur **Nouveau**.

5. Dans la boîte de dialogue **Ajouter un nouveau composant**, affectez à **Type** la valeur **Microsoft.VisualStudio.VsPackage**, à **Source** la valeur **Fichier sur le système de fichiers** et à **Chemin d’accès** la valeur **HelloWorldVB.pkgdef** (qui doit apparaître dans la liste déroulante).

### <a name="test-the-snippet"></a>Testez l’extrait

1. À présent, vous pouvez vous assurer que l'extrait de code fonctionne dans l'instance expérimentale de Visual Studio. L'instance expérimentale est une seconde copie de Visual Studio, distincte de celle que vous utilisez pour écrire le code. Elle vous permet de travailler sur une extension sans affecter votre environnement de développement.

2. Générez le projet et commencez le débogage.

   Une seconde instance de Visual Studio apparaît.

3. Dans l’instance expérimentale, accédez à **Outils** > **Gestionnaire des extraits de code**, puis affectez à **Langage** la valeur **Basic**. En principe, vous devez voir *HelloWorldVB* parmi les dossiers, et vous devez pouvoir développer ce dossier pour afficher l’extrait *HelloWorldVB*.

4. Testez l'extrait de code. Dans l'instance expérimentale, ouvrez un projet Visual Basic et ouvrez l'un des fichiers de code. Placez votre curseur quelque part dans le code, effectuez un clic droit et, dans le menu contextuel, sélectionnez **Insérer un extrait**.

5. Normalement, vous devez voir *HelloWorldVB* parmi les dossiers. Double-cliquez dessus. Vous devez voir une fenêtre contextuelle **Insérer un extrait : HelloWorldVB >** comportant une liste déroulante **HelloWorldVB**. Cliquez sur la liste déroulante **HelloWorldVB**.

   La ligne suivante est ajoutée au fichier de code :

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../ide/code-snippets.md)