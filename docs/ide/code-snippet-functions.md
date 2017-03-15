---
title: "Fonctions des extraits de code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extraits de code (Visual Studio), fonctions"
  - "extraits de code IntelliSense, fonctions"
  - "extraits (Visual Studio), fonctions"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Fonctions des extraits de code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il est possible d'utiliser trois fonctions avec les extraits de code en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Les fonctions sont spécifiées dans l'élément [Function](http://msdn.microsoft.com/fr-fr/572c5549-5821-4e15-8ecd-0fa86c1c65df) de l'extrait de code.  Pour plus d'informations sur la création d'extraits de code, consultez [Extraits de code](../ide/code-snippets.md).  
  
## Fonctions  
 Le tableau suivant décrit les fonctions que vous pouvez utiliser avec l'élément `Function` dans les extraits de code.  
  
|Fonction|Description|Language|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Génère une instruction switch et un jeu d'instructions case pour les membres de l'énumération spécifiée par le paramètre `EnumerationLiteral`.  Le paramètre `EnumerationLiteral` doit être soit une référence à un littéral d'énumération soit un type d'énumération.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Retourne le nom de la classe qui contient l'extrait inséré.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Réduit le paramètre  *TypeName* à sa forme la plus simple dans le contexte où l'extrait de code a été appelé.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## Exemple  
 L'exemple suivant montre comment utiliser la fonction `GenerateSwitchCases`.  Lorsque cet extrait de code est inséré et qu'une énumération est introduite dans le littéral `$switch_on$`, le littéral `$cases$` génère une instruction `case` pour chaque valeur dans l'énumération.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Exemple  
 L'exemple suivant montre comment utiliser la fonction `ClassName`.  Lorsque cet extrait de code est inséré, le littéral `$classname$` est remplacé par le nom de la classe englobante à cet emplacement dans le fichier de code.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Exemple  
 Cet exemple indique comment utiliser la fonction `SimpleTypeName`.  Lorsque cet extrait de code est inséré dans un fichier de code, le littéral `$SystemConsole$` sera remplacé par la forme la plus simple du type <xref:System.Console> dans le contexte dans lequel l'extrait de code a été appelé.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Voir aussi  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/fr-fr/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)