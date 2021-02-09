---
title: 'Procédure pas à pas : Créer un extrait de code'
description: 'Découvrez comment créer un extrait de code en trois étapes : créer un fichier XML, remplir les éléments appropriés et y ajouter votre code.'
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 39565b95b93e489a739c2da3a0f88fb9f683a2bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873799"
---
# <a name="walkthrough-create-a-code-snippet"></a>Procédure pas à pas : Créer un extrait de code

Vous pouvez créer un extrait de code en quelques étapes seulement. Il vous suffit de créer un fichier XML, de le remplir avec les éléments appropriés et d’y ajouter votre code. Vous pouvez utiliser des paramètres de remplacement et des références de projet. Importez l’extrait de code dans votre installation Visual Studio en utilisant le bouton **Importer** dans le **Gestionnaire des extraits de code** (**Outils** > **Gestionnaire des extraits de code**).

## <a name="snippet-template"></a>Modèle d’extrait de code

Le code XML suivant est le modèle d’extrait de code de base :

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Créer un extrait de code

1. Créez un fichier XML dans Visual Studio et ajoutez-y le modèle ci-dessus.

2. Entrez un titre pour l’extrait de code dans l’élément **Title**. Utilisez le titre **Square Root**.

3. Indiquez le langage de l’extrait dans l’attribut **Languages** de l’élément **Code**. Pour C#, utilisez **CSharp**, pour Visual Basic, utilisez **VB** et pour C++, utilisez **CPP**.

   > [!TIP]
   > Pour voir toutes les valeurs de langue disponibles, parcourez la [section Attributs de l’élément de code](code-snippets-schema-reference.md#attributes) dans la page [Référence de schéma des extraits de code](code-snippets-schema-reference.md).

4. Ajoutez le code de l’extrait de code dans la section **CDATA** de l’élément **Code**.

   Pour C# :

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Ou, pour Visual Basic :

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Vous ne pouvez pas spécifier la façon dont les lignes de code dans la section **CDATA** d’un extrait de code doivent indentées ou mises en forme. Lors de l’insertion, le service de langage met en forme le code inséré automatiquement.

5. Enregistrez l’extrait de code en tant que *SquareRoot.snippet* (vous pouvez l’enregistrer à n’importe quel emplacement).

## <a name="import-a-code-snippet"></a>Importer un extrait de code

1. Vous pouvez importer un extrait de code dans votre installation Visual Studio en utilisant le **Gestionnaire des extraits de code**. Ouvrez-le en choisissant **Outils**  >  **Gestionnaire des extraits de code**.

2. Cliquez sur le bouton **Import**.

3. Accédez à l’emplacement où vous avez enregistré l’extrait de code dans la procédure précédente, sélectionnez-le, puis cliquez sur **Ouvrir**.

4. La boîte de dialogue **Importer un extrait de code** s’ouvre et vous invite à choisir l’emplacement où ajouter l’extrait de code parmi les emplacements proposés dans le volet droit. **My Code Snippets** (Mes extraits de code) est l’une de ces propositions. Sélectionnez-la, puis cliquez sur **Terminer**, puis sur **OK**.

5. L’extrait de code est copié à un des emplacements suivants, selon le langage du code :

   ::: moniker range="vs-2017"

   *Extraits de code C# \Mes%USERPROFILE%\Documents\Visual Studio 2017 \ code Snippets\Visual*  
   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019 \ code Snippets\Visual C# \Mes code extraits de code*  
   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. Testez votre extrait de code en ouvrant un projet C# ou Visual Basic. Quand un fichier de code est ouvert dans l’éditeur, choisissez **extraits**  >  **Insérer un extrait** dans le menu contextuel, puis **mes extraits de code**. Vous devez voir un extrait de code nommé **Square Root**. Double-cliquez dessus.

   L’extrait de code est inséré dans le fichier de code.

## <a name="description-and-shortcut-fields"></a>Champs de description et de raccourci

::: moniker range="vs-2017"

1. Les champs Description donnent des informations supplémentaires sur votre extrait de code affiché dans le Gestionnaire des extraits de code. Le raccourci est une balise que les utilisateurs peuvent entrer pour insérer votre extrait de code. Pour modifier l’extrait de code que vous avez ajouté, ouvrez le fichier *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# ou Visual Basic]\My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Les champs Description donnent des informations supplémentaires sur votre extrait de code affiché dans le Gestionnaire des extraits de code. Le raccourci est une balise que les utilisateurs peuvent entrer pour insérer votre extrait de code. Pour modifier l’extrait de code que vous avez ajouté, ouvrez le fichier *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# ou Visual Basic]\My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Comme vous modifiez le fichier dans le répertoire où Visual Studio l’a placé, vous n’avez pas besoin de le réimporter dans Visual Studio.

2. Ajoutez des éléments d' **auteur** et de **Description** à l’élément d' **en-tête** , puis remplissez-les.

3. L’élément d' **en-tête** doit se présenter comme suit :

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Ouvrez le **Gestionnaire des extraits de code** et sélectionnez votre extrait de code. Dans le volet droit, notez que les champs **Description** et **Author** sont maintenant renseignés.

   ![Description de l’extrait de code dans le Gestionnaire des extraits de code](media/code-snippet-description-author.png)

5. Pour ajouter un raccourci, ajoutez un élément **Shortcut** dans l’élément **Header** :

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Enregistrez de nouveau le fichier d’extrait de code.

7. Pour tester le raccourci, ouvrez le projet que vous avez utilisé précédemment, puis tapez **sqrt** dans l’éditeur et appuyez sur **Tab** (une fois pour Visual Basic, deux fois pour C#).

   L’extrait de code est inséré.

## <a name="replacement-parameters"></a>Paramètres de remplacement

Vous pouvez souhaiter que des parties d’un extrait de code soient remplacées par l’utilisateur. Par exemple, vous voulez que l’utilisateur remplace un nom de variable par une variable de son projet. Vous pouvez ajouter deux types de remplacements : des littéraux et des objets. Utilisez l’[élément Literal](code-snippets-schema-reference.md#literal-element) pour identifier le remplacement d’une partie de code entièrement contenue dans l’extrait de code, mais qui sera probablement personnalisée après avoir été insérée dans le code (par exemple une chaîne ou une valeur numérique). Utilisez l’[élément Object](code-snippets-schema-reference.md#object-element) pour identifier un élément qui est nécessaire dans l’extrait de code, mais qui est probablement défini en dehors de l’extrait de code lui-même (par exemple une instance d’objet ou un contrôle).

1. Pour permettre à l’utilisateur de remplacer facilement le nombre dont la racine carrée doit être calculée, modifiez l’élément **Snippet** du fichier *SquareRoot.snippet* comme suit :

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Notez que le remplacement du littéral reçoit un ID (`Number`). Cet ID est référencé depuis l’extrait de code en l’entourant de caractères `$` :

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Enregistrez le fichier d’extrait de code.

3. Ouvrez un projet et insérez l’extrait de code.

   L’extrait de code est inséré et le littéral modifiable est mis en surbrillance pour le remplacement. Pointez sur le paramètre de remplacement pour afficher l’info-bulle indiquant la valeur.

   ![Info-bulle du paramètre de remplacement de l’extrait de code dans Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > S’il existe plusieurs paramètres remplaçables dans un extrait de code, vous pouvez appuyer sur **Tab** pour passer d’un paramètre à l’autre et modifier les valeurs.

## <a name="import-a-namespace"></a>Importer un espace de noms

Vous pouvez utiliser un extrait de code pour ajouter une directive `using` (C#) ou une instruction `Imports` (Visual Basic) en incluant l’[élément Imports](code-snippets-schema-reference.md#imports-element). Pour les projets .NET Framework, vous pouvez également ajouter une référence au projet en utilisant l’[élément References](code-snippets-schema-reference.md#references-element).

Le code XML suivant montre un extrait de code qui utilise la méthode `File.Exists` dans l’espace de noms System.IO, et qui définit donc l’élément **Imports** pour importer l’espace de noms System.IO.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Voir aussi

- [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)
