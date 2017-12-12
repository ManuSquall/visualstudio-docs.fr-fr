---
title: Fonctions des extraits de code | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0628e118ecf0d22591ff1f88208e2cc5396a6bc4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="code-snippet-functions"></a>Fonctions des extraits de code
Trois fonctions peuvent être utilisées avec les extraits de code [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Les fonctions sont spécifiées dans l’élément [Function](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df) de l’extrait de code. Pour plus d’informations sur la création d’extraits de code, consultez [Extraits de code](../ide/code-snippets.md).  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant décrit les fonctions qui peuvent être utilisées avec l’élément `Function` dans les extraits de code.  
  
|Fonction|Description|Langage|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Génère une instruction switch et un ensemble d’instructions case pour les membres de l’énumération spécifiée par le paramètre `EnumerationLiteral`. Le paramètre `EnumerationLiteral` doit être une référence à un littéral d’énumération ou un type d’énumération.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Retourne le nom de la classe qui contient l’extrait de code inséré.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Réduit le paramètre *TypeName* à sa forme la plus simple dans le contexte dans lequel l’extrait de code a été appelé.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la fonction `GenerateSwitchCases`. Quand cet extrait de code est inséré et qu’une énumération est entrée dans le littéral `$switch_on$`, le littéral `$cases$` génère une instruction `case` pour chaque valeur contenue dans l’énumération.  
  
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
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la fonction `ClassName`. Quand cet extrait de code est inséré, le littéral `$classname$` est remplacé par le nom de la classe englobante à cet emplacement dans le fichier de code.  
  
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
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser la fonction `SimpleTypeName`. Quand cet extrait de code est inséré dans un fichier de code, le littéral `$SystemConsole$` est remplacé par la forme la plus simple du type <xref:System.Console> dans le contexte dans lequel l’extrait de code a été appelé.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Function, élément (extraits de code IntelliSense)](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)