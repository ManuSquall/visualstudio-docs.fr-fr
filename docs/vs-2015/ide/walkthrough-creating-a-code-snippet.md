---
title: 'Procédure pas à pas : Création d’un extrait de Code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9b09a8990de97357da2703f1d08dabec50ea75e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790111"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Procédure pas à pas : création d'un extrait de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer un extrait de code en quelques étapes seulement. Il vous suffit de créer un fichier XML, de le remplir avec les éléments appropriés et d’y ajouter votre code. Vous pouvez aussi ajouter des références et des paramètres de remplacement dans votre code. Vous pouvez ensuite ajouter l’extrait de code à votre installation Visual Studio à l’aide du bouton Importer dans le Gestionnaire des extraits de code (**Outils/Gestionnaire des extraits de code**).  
  
> [!TIP]
>  Pour plus d’informations sur la façon d’écrire plus facilement les extraits de code, recherche le site Web CodePlex pour les outils de la Communauté telles que [Snippet Editor](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## <a name="snippet-template"></a>Modèle d’extrait de code  
 Voici le modèle d’extrait de code de base :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
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
  
### <a name="to-create-a-code-snippet"></a>Pour créer un extrait de code  
  
1.  Créez un fichier XML dans Visual Studio et ajoutez-y le modèle ci-dessus.  
  
2.  Entrez un titre pour l’extrait de code (par exemple, « Hello World VB ») dans l’élément Title.  
  
3.  Spécifiez le langage de l’extrait de code dans l’attribut Languages de l’élément Code. Pour cet exemple, entrez « VB ».  
  
4.  Ajoutez du code dans la section CDATA de l’élément Code, par exemple :  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Enregistrez l’extrait de code sous le nom VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Pour ajouter un extrait de code dans Visual Studio  
  
1.  Vous pouvez ajouter vos propres extraits de code à votre installation Visual Studio par le biais du Gestionnaire des extraits de code. Ouvrez le Gestionnaire des extraits de code (**Outils/Gestionnaire des extraits de code**).  
  
2.  Cliquez sur le bouton **Importer**.  
  
3.  Accédez à l’emplacement où vous avez enregistré l’extrait de code dans la procédure précédente, sélectionnez-le, puis cliquez sur **Ouvrir**.  
  
4.  La boîte de dialogue **Importer un extrait de code** s’ouvre et vous invite à choisir l’emplacement où ajouter l’extrait de code parmi les emplacements proposés dans le volet droit. **My Code Snippets** (Mes extraits de code) est l’une de ces propositions. Sélectionnez-la, puis cliquez sur **Terminer**, puis sur **OK**.  
  
5.  L’extrait de code est copié à l’emplacement suivant :  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Testez votre extrait de code en ouvrant un projet Visual Basic et un fichier de code. Dans le fichier, cliquez sur **insérer un extrait** dans le menu contextuel, puis **mes extraits de Code**. Vous devez normalement voir un extrait de code nommé **My Visual Basic Code Snippet** (Mon extrait de code Visual Basic). Double-cliquez dessus.  
  
7.  Vous devriez voir `Console.WriteLine("Hello, World!")` inséré dans le code.  
  
### <a name="adding-description-and-shortcut-fields"></a>Ajout de champs Description et Raccourci  
  
1.  Les champs Description donnent des informations supplémentaires sur votre extrait de code affiché dans le Gestionnaire des extraits de code. Le raccourci est une balise que les utilisateurs peuvent entrer pour insérer votre extrait de code. Modifier l’extrait de code que vous avez ajouté en ouvrant le fichier `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Ajoutez les éléments Author et Description dans l’élément Header, puis renseignez-les.  
  
3.  L’élément Header doit ressembler à ceci :  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Ouvrez le Gestionnaire des extraits de code et sélectionnez votre extrait de code. Dans le volet droit, les champs Description et Author doivent maintenant être renseignés.  
  
5.  Pour ajouter un raccourci, ajoutez un élément Shortcut en dessous des éléments Author et Description :  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Enregistrez de nouveau le fichier d’extrait de code.  
  
7.  Pour tester le raccourci, ouvrez un projet Visual Basic et un fichier de code. Type `hello` dans le fichier et appuyez sur TAB. L’extrait de code doit être inséré.  
  
### <a name="to-add-references-and-imports"></a>Pour ajouter des références et des importations  
  
1.  Avec des extraits de code Visual Basic, vous pouvez ajouter une référence à un projet à l’aide de l’élément References et ajouter une déclaration Imports à l’aide de l’élément Imports. (Les extraits de code dans d’autres langages n’ont pas cette fonctionnalité.) Par exemple, si vous remplacez `Console.WriteLine` par `MessageBox.Show` dans l’exemple de code, vous pouvez avoir besoin d’ajouter l’assembly System.Windows.Forms.dll au projet.  
  
2.  Ouvrez votre extrait de code.  
  
3.  Ajoutez l’élément References sous l’élément Snippet :  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Ajoutez l’élément Imports sous l’élément Snippet :  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Modifiez la section CDATA de la façon suivante :  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Enregistrez l’extrait de code.  
  
7.  Ouvrez un projet Visual Basic et ajoutez l’extrait de code.  
  
8.  Il y a maintenant une instruction Imports en haut du fichier de code :  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Examinez les propriétés du projet. L’onglet Références affiche une référence à System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Ajout de remplacements  
  
1.  Vous souhaitez peut-être que certaines parties de votre extrait de code soient remplacées par l’utilisateur, par exemple, si vous ajoutez une variable que l’utilisateur doit remplacer par une valeur dans le projet actuel. Vous pouvez ajouter deux types de remplacements : des littéraux et des objets. Les littéraux sont des chaînes d’un type donné (littéraux de chaîne, noms de variable ou représentations sous forme de chaînes de valeurs numériques). Les objets sont des instances d’un type autre qu’une chaîne. Dans cette procédure, vous allez déclarer un remplacement de littéral et un remplacement d’objet, puis modifier le code pour faire référence à ces remplacements.  
  
2.  Ouvrez votre extrait de code.  
  
3.  Cet exemple utilise une chaîne de connexion SQL. Vous devez changer les éléments Imports et References pour ajouter les références appropriées :  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  Pour déclarer un remplacement de littéral pour la chaîne de connexion SQL, ajoutez un élément Declarations sous l’élément Snippet et, à l’intérieur du nouvel élément, ajoutez un élément Literal et des sous-éléments pour l’ID, l’info-bulle et la valeur par défaut du remplacement :  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Pour déclarer un remplacement d’objet pour la connexion SQL, ajoutez un élément Object à l’intérieur de l’élément Declarations et ajoutez des sous-éléments pour l’ID, le type de l’objet, l’info-bulle et la valeur par défaut. L’élément Declarations obtenu doit ressembler à ceci :  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  Dans la section Code, référencez les remplacements en les entourant de signes $, par exemple `$replacement$` :  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  Enregistrez l’extrait de code.  
  
8.  Ouvrez un projet Visual Basic et ajoutez l’extrait de code.  
  
9. Le code doit ressembler à l’exemple ci-dessous, où les remplacements `SQL connection string` et `dcConnection` sont indiqués en orange clair. Appuyez sur TAB pour accéder à partir d’un à l’autre.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)
