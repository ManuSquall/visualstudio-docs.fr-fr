---
title: Guide pratique pour distribuer des extraits de code | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bda2aa5e7639b951b0df6bb83ff2d50fd4331e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495393"
---
# <a name="how-to-distribute-code-snippets"></a>Guide pratique pour distribuer des extraits de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : distribuer des extraits de Code](https://docs.microsoft.com/visualstudio/ide/how-to-distribute-code-snippets).  
  
Vous pouvez vous contenter de donner vos extraits de code à vos amis pour qu'ils les installent sur leurs propres ordinateurs à l'aide du Gestionnaire des extraits de code. Toutefois, si vous avez plusieurs extraits de code à distribuer ou que vous souhaitez les distribuer plus largement, vous pouvez inclure votre fichier d'extraits de code dans une extension Visual Studio, que les utilisateurs de Visual Studio peuvent installer.  
  
 Vous devez installer le kit SDK Visual Studio pour pouvoir créer des extensions Visual Studio. Recherchez la version du SDK Visual Studio qui correspond à votre installation de Visual Studio dans [téléchargements de Visual Studio 2015](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx).  
  
## <a name="setting-up-the-extension"></a>Configuration de l’extension  
 Dans cette procédure, nous utiliserons l’extrait de code Hello World qui a été créé dans [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md). Nous fournirons le texte .snippet afin que vous n'ayez pas à revenir en arrière et à en créer un.  
  
1.  Créez un projet VSIX nommé **TestSnippet**. (**Fichier / Nouveau / Projet / Visual C# (ou Visual Basic) / Extensibilité**)  
  
2.  Dans le projet **TestSnippet**, ajoutez un nouveau fichier XML et appelez-le **VBCodeSnippet.snippet**. Remplacez le contenu par celui-ci :  
  
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
  
#### <a name="setting-up-the-directory-structure"></a>Configuration de la structure de répertoires  
  
1.  Dans l’Explorateur de solutions, sélectionnez le nœud du projet et ajoutez un dossier portant le nom que vous souhaitez donner à l’extrait de code dans le Gestionnaire des extraits de code. Dans le cas présent, ce doit être **HelloWorldVB**.  
  
2.  Déplacez le fichier .snippet vers le dossier **HelloWorldVB**.  
  
3.  Sélectionnez le fichier .snippet dans l’Explorateur de solutions et, dans la fenêtre **Propriétés**, veillez à ce que **Action de génération** ait la valeur **Contenu**, que **Copier dans le répertoire de sortie** ait la valeur **Toujours copier** et que **Inclure dans VSIX** ait la valeur **true**.  
  
#### <a name="adding-the-pkgdef-file"></a>Ajout du fichier .pkgdef  
  
1.  Ajoutez un fichier texte dans le dossier **HelloWorldVB** et nommez-le **HelloWorldVB.pkgdef**. Ce fichier permet d'ajouter certaines clés dans le Registre. Dans le cas présent, il ajoute une nouvelle clé dans  
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.  
  
2.  Ajoutez les lignes ci-dessous au fichier.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Si vous examinez cette clé, vous pouvez voir comment spécifier des langues différentes.  
  
3.  Sélectionnez le fichier .pkgdef dans l’Explorateur de solutions et, dans la fenêtre **Propriétés**, veillez à ce que **Action de génération** ait la valeur **Contenu**, que **Copier dans le répertoire de sortie** ait la valeur **Toujours copier** et que **Inclure dans VSIX** ait la valeur **true**.  
  
4.  Ajoutez le fichier .pkgdef en tant que ressource dans le manifeste VSIX. Dans le fichier source.extension.vsixmanifest, affichez l’onglet **Ressources** et cliquez sur **Nouveau**.  
  
5.  Dans la boîte de dialogue **Ajouter un nouveau composant**, affectez à **Type** la valeur **Microsoft.VisualStudio.VsPackage**, à **Type** la valeur **Fichier sur le système de fichiers** et à **Chemin d’accès** la valeur **HelloWorldVB.pkgdef** (qui doit apparaître dans la liste déroulante).  
  
### <a name="testing-the-snippet"></a>Test de l'extrait de code  
  
1.  À présent, vous pouvez vous assurer que l'extrait de code fonctionne dans l'instance expérimentale de Visual Studio. L'instance expérimentale est une seconde copie de Visual Studio, distincte de celle que vous utilisez pour écrire le code. Elle vous permet de travailler sur une extension sans affecter votre environnement de développement.  
  
2.  Générez le projet et commencez le débogage. Une seconde instance de Visual Studio doit apparaître.  
  
3.  Dans l’instance expérimentale, accédez à **Outils / Gestionnaire des extraits de code** et affectez à **Langage** la valeur **Basic**. Vous devez normalement voir HelloWorldVB parmi les dossiers et vous devez être en mesure de développer ce dossier pour afficher l’extrait de code HelloWorldVB.  
  
4.  Testez l'extrait de code. Dans l'instance expérimentale, ouvrez un projet Visual Basic et ouvrez l'un des fichiers de code. Placez votre curseur quelque part dans le code, effectuez un clic droit et, dans le menu contextuel, sélectionnez **Insérer un extrait**.  
  
5.  Vous devez normalement voir HelloWorldVB parmi les dossiers. Double-cliquez dessus. Vous devez normalement voir une fenêtre contextuelle **Insérer un extrait : HellowWorldVB >** comportant une liste déroulante **HelloWorldVB**. Cliquez sur la liste déroulante HelloWorldVB. La ligne suivante doit normalement être ajoutée au fichier :  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Extraits de code](../ide/code-snippets.md)



