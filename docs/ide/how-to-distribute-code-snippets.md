---
title: Guide pratique pour distribuer des extraits de code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: e867bafff9c41aff525557484189693950b7b468
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-distribute-code-snippets"></a>Guide pratique pour distribuer des extraits de code

Vous pouvez donner des extraits de code à vos amis pour qu’ils les installent sur leurs ordinateurs à l’aide du Gestionnaire des extraits de code. Toutefois, si vous avez plusieurs extraits de code à distribuer ou que vous souhaitez les distribuer plus largement, vous pouvez inclure votre fichier d'extraits de code dans une extension Visual Studio, que les utilisateurs de Visual Studio peuvent installer.

Vous devez installer le kit SDK Visual Studio pour pouvoir créer des extensions Visual Studio. Recherchez la version du kit SDK Visual Studio qui correspond à votre installation de Visual Studio dans la page [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/).

## <a name="set-up-the-extension"></a>Configurer l’extension

Au cours de cette procédure, nous allons utiliser l’extrait de code Hello World créé dans [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md). Nous fournirons le texte du fichier *.snippet* pour que vous n’ayez pas à revenir en arrière afin d’en créer un.

1.  Créez un projet VSIX nommé **TestSnippet**. (**Fichier** > **Nouveau** > **Projet** > **Visual C# (ou Visual Basic)** > **Extensibilité**.)

2.  Dans le projet **TestSnippet**, ajoutez un nouveau fichier XML et appelez-le *VBCodeSnippet.snippet*. Remplacez le contenu par celui-ci :

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

1.  Dans l’**Explorateur de solutions**, sélectionnez le nœud de projet et ajoutez un dossier portant le nom que vous souhaitez donner à l’extrait dans le **Gestionnaire des extraits de code**. Dans le cas présent, il doit s’agir de **HelloWorldVB**.

2.  Déplacez le fichier *.snippet* vers le dossier *HelloWorldVB*.

3.  Sélectionnez le fichier *.snippet* dans l’**Explorateur de solutions**. Dans la fenêtre **Propriétés**, vérifiez que **Action de génération** a la valeur **Contenu**, que **Copier dans le répertoire de sortie** a la valeur **Toujours copier** et que **Inclure dans VSIX** a la valeur **true**.

### <a name="add-the-pkgdef-file"></a>Ajouter le fichier .pkgdef

1.  Ajoutez un fichier texte dans le dossier *HelloWorldVB* et nommez-le *HelloWorldVB.pkgdef*. Ce fichier permet d'ajouter certaines clés dans le Registre. Dans le cas présent, il ajoute une nouvelle clé dans :

     `HKCU\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic`

2.  Ajoutez les lignes ci-dessous au fichier.

    ```
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Si vous examinez cette clé, vous pouvez voir comment spécifier des langues différentes.

3.  Sélectionnez le fichier *.pkgdef* dans l’**Explorateur de solutions**. Dans la fenêtre **Propriétés**, vérifiez que **Action de génération** a la valeur **Contenu**, que **Copier dans le répertoire de sortie** a la valeur **Toujours copier** et que **Inclure dans VSIX** a la valeur **true**.

4.  Ajoutez le fichier *.pkgdef* en tant que composant dans le manifeste VSIX. Dans le fichier *source.extension.vsixmanifest*, accédez à l’onglet **Ressources**, puis cliquez sur **Nouveau**.

5.  Dans la boîte de dialogue **Ajouter un nouveau composant**, affectez à **Type** la valeur **Microsoft.VisualStudio.VsPackage**, à **Source** la valeur **Fichier sur le système de fichiers** et à **Chemin d’accès** la valeur **HelloWorldVB.pkgdef** (qui doit apparaître dans la liste déroulante).

### <a name="test-the-snippet"></a>Testez l’extrait

1.  À présent, vous pouvez vous assurer que l'extrait de code fonctionne dans l'instance expérimentale de Visual Studio. L'instance expérimentale est une seconde copie de Visual Studio, distincte de celle que vous utilisez pour écrire le code. Elle vous permet de travailler sur une extension sans affecter votre environnement de développement.

2.  Générez le projet et commencez le débogage. Une seconde instance de Visual Studio doit apparaître.

3.  Dans l’instance expérimentale, accédez à **Outils > Gestionnaire des extraits de code**, puis affectez à **Langage** la valeur **Basic**. En principe, vous devez voir *HelloWorldVB* parmi les dossiers, et vous devez pouvoir développer ce dossier pour afficher l’extrait *HelloWorldVB*.

4.  Testez l'extrait de code. Dans l'instance expérimentale, ouvrez un projet Visual Basic et ouvrez l'un des fichiers de code. Placez votre curseur quelque part dans le code, effectuez un clic droit et, dans le menu contextuel, sélectionnez **Insérer un extrait**.

5.  Normalement, vous devez voir *HelloWorldVB* parmi les dossiers. Double-cliquez dessus. Vous devriez normalement voir la fenêtre contextuelle **Insérer un extrait : HelloWorldVB >** comportant une liste déroulante **HelloWorldVB**. Cliquez sur la liste déroulante **HelloWorldVB**. La ligne suivante doit normalement être ajoutée au fichier :

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../ide/code-snippets.md)