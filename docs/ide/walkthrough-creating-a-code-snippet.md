---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un extrait de code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extraits de code, créer"
  - "extraits de code, importations"
  - "extraits de code, références"
  - "extraits de code, remplacements"
  - "extraits de code, raccourci"
  - "extraits de code, modèle"
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un extrait de code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez créer un extrait de code en quelques étapes.  Il vous suffit de créer un fichier XML, de compléter les éléments appropriés, et d'y ajouter votre le code.  Vous pouvez également ajouter des références et des paramètres de remplacement à votre code.  Vous pouvez ajouter l'extrait de code à votre installation Visual Studio à l'aide du bouton Importer du Gestionnaire des extraits de code \(**Outils\/Gestionnaire des extraits de code**\).  
  
> [!TIP]
>  Pour plus d'informations sur l'écriture d'extraits de code facilement, recherchez le site Web CodePlex pour les outils de communauté comme [Éditeur d'extrait de code](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## Modèle d'extrait de code  
 Voici le modèle d'extrait de code de base :  
  
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
  
### Pour créer un extrait de code.  
  
1.  Créez un fichier XML dans Visual Studio et ajoutez le modèle ci\-dessus.  
  
2.  Complétez le titre de l'extrait de code, par exemple « Hello World VB », dans l'élément d'en\-tête.  
  
3.  Complétez le langage de l'extrait de code dans l'attribut Langues de l'élément Code.  Pour cet exemple, utilisez « VB ».  
  
4.  Ajoutez du code dans la section CDATA dans l'élément de code, par exemple :  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Enregistrez l'extrait de code comme VBCodeSnippet.snippet.  
  
### Pour ajouter un extrait de code à Visual Studio  
  
1.  Vous pouvez ajouter vos propres extraits de code à votre installation Visual Studio à l'aide du Gestionnaire des extraits de code.  Ouvrez le Gestionnaire des extraits de code \(**Outils\/Gestionnaire des extraits de code**\).  
  
2.  Cliquez sur le bouton **Importer**.  
  
3.  Accédez à l'emplacement où vous avez enregistré l'extrait de code dans la procédure précédente, sélectionnez\-la, puis cliquez sur **Ouvrir**.  
  
4.  La boîte de dialogue **Importer un extrait de code** s'ouvre, pour vous demander de choisir l'emplacement où ajouter l'extrait de code parmi les options disponibles dans le volet droit.  Un des choix doit être **Mes extraits de code**.  Sélectionnez\-le, cliquez sur **Terminer**, puis sur **OK**.  
  
5.  L'extrait de code est copié dans l'emplacement suivant :  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Testez votre extrait de code en ouvrant un projet Visual Basic et en ouvrant un fichier de code.  Dans le fichier, cliquez sur **Insérer l'extrait** dans le menu contextuel, puis sur **Mes extraits de code**.  Un extrait de code nommé **Mon extrait de code Visual Basic** doit s'afficher.  Double\-cliquez dessus.  
  
7.  `Console.WriteLine("Hello, World!")` doit être inséré dans le code.  
  
### Ajout de champs Description et Raccourcis  
  
1.  Les champs de description fournissent des informations sur votre extrait de code une fois affiché dans le Gestionnaire des extraits de code.  Le raccourci est une balise que les utilisateurs peuvent taper pour insérer votre extrait de code.  Modifiez l'extrait de code que vous avez ajouté en ouvrant le fichier `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Ajoutez des éléments d'auteur et de description à l'élément d'en\-tête, et complétez\- les.  
  
3.  L'élément d'en\-tête doit ressembler à ce qui suit :  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Ouvrez le Gestionnaire des extraits de code et sélectionnez votre extrait de code.  Dans le volet droit vous devriez voir que les champs Description et Auteur sont maintenant remplis.  
  
5.  Pour ajouter un raccourci, ajoutez un élément Raccourci à côté de l'élément Auteur et Description :  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Enregistrez le fichier d'extrait et réessayez.  
  
7.  Pour tester le raccourci, ouvrez un projet Visual Basic et ouvrez un fichier de code.  Tapez `hello` dans le fichier et appuyez sur TAB.  L'extrait de code doit être inséré.  
  
### Pour ajouter des importations et des références  
  
1.  Avec les extraits de code Visual Basic, vous pouvez ajouter une référence à un projet en utilisant l'élément References, puis ajouter une déclaration Imports en utilisant l'élément Imports. \(Les extraits de code d'autres langages n'ont pas cette fonctionnalité.\) Par exemple, si vous modifiez `Console.WriteLine` dans l'exemple de code pour `MessageBox.Show`, vous devrez peut\-être ajouter l'assembly System.Windows.Forms.dll au projet.  
  
2.  Ouvrez votre extrait de code.  
  
3.  Ajoutez l'élément Références sous l'élément d'extrait de code :  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Ajoutez l'élément d'importations sous l'élément d'extrait de code :  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Modifiez la section CDATA comme suit :  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Enregistrez l'extrait de code.  
  
7.  Ouvrez un projet Visual Basic et ajoutez l'extrait de code.  
  
8.  Une instruction Imports s'affichera en haut du fichier de code :  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Examinez les propriétés du projet.  L'onglet Références inclut une référence à System.Windows.Forms.dll.  
  
### Ajout de Remplacements  
  
1.  Vous souhaitez peut\-être que des parties de vos extraits de code soient remplacées par l'utilisateur, par exemple si vous ajoutez une variable et souhaitez que l'utilisateur la remplace par une variable dans le projet actuel.  Vous pouvez fournir deux types de remplacements : littéraux et objets.  Les littéraux sont des chaînes d'un certain type \(littéraux de chaîne, noms de variables ou représentations sous forme de chaîne de valeurs numériques\).  Les objets sont des instances d'un type autre qu'une chaîne.  Dans cette procédure vous déclarez un remplacement littéral et un remplacement d'objet, et modifiez le code pour référencer ces remplacements.  
  
2.  Ouvrez votre extrait de code.  
  
3.  Cet exemple utilise une chaîne de connexion SQL, vous devez donc modifier les éléments Imports et References pour ajouter les références appropriées :  
  
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
  
4.  Pour déclarer un remplacement littéral pour la chaîne de connexion SQL, ajoutez un élément Declarations sous l'élément Snippet, puis ajoutez\-lui un élément Literal contenant des sous\-éléments pour l'ID, l'info\-bulle et la valeur par défaut du remplacement :  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Pour déclarer un remplacement d'objet pour la connexion SQL, ajoutez un élément Object dans l'élément Declarations et ajoutez des sous\-éléments pour l'ID, le type de l'objet, l'info\-bulle et la valeur par défaut.  L'élément Declarations obtenu doit se présenter comme suit :  
  
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
  
6.  Dans la section de code, référencez les remplacements entourés des signes $, par exemple `$replacement$`:  
  
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
  
7.  Enregistrez l'extrait de code.  
  
8.  Ouvrez un projet Visual Basic et ajoutez l'extrait de code.  
  
9. Le code doit se présenter comme suit, les remplacements `Chaîne de connexion SQL` et `dcConnection` étant mis en surbrillance en orange clair.  Appuyez sur la touche de tabulation pour naviguer de l'un à l'autre.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## Voir aussi  
 [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)