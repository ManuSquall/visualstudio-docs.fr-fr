---
title: Fonctions des extraits de code
description: Découvrez les fonctions GenerateSwitchCases (EnumerationLiteral), ClassName () et SimpleTypeName (TypeName) qui peuvent être utilisées avec les extraits de code C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce569dabca9e5d867310b8d510975331f5a9f046
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954434"
---
# <a name="code-snippet-functions"></a>Fonctions des extraits de code

Trois fonctions peuvent être utilisées avec les extraits de code C#. Les fonctions sont spécifiées dans l’élément [Function](../ide/code-snippets-schema-reference.md#function-element) de l’extrait de code. Pour plus d’informations sur la création d’extraits de code, consultez [Extraits de code](../ide/code-snippets.md).

## <a name="functions"></a>Fonctions

Le tableau suivant décrit les fonctions qui peuvent être utilisées avec l’élément `Function` dans les extraits de code.

|Fonction|Description|Language|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Génère une instruction switch et un ensemble d’instructions case pour les membres de l’énumération spécifiée par le paramètre `EnumerationLiteral`. Le paramètre `EnumerationLiteral` doit être une référence à un littéral d’énumération ou un type d’énumération.|C#|
|`ClassName()`|Retourne le nom de la classe qui contient l’extrait de code inséré.|C#|
|`SimpleTypeName(TypeName)`|Réduit le paramètre *TypeName* à sa forme la plus simple dans le contexte dans lequel l’extrait de code a été appelé.|C#|

## <a name="generateswitchcases-example"></a>Exemple de GenerateSwitchCases

L’exemple suivant explique comment utiliser la fonction `GenerateSwitchCases`. Quand cet extrait de code est inséré et qu’une énumération est entrée dans le littéral `$switch_on$`, le littéral `$cases$` génère une instruction `case` pour chaque valeur contenue dans l’énumération.

```xml
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

## <a name="classname-example"></a>Exemple de ClassName

L’exemple suivant explique comment utiliser la fonction `ClassName`. Quand cet extrait de code est inséré, le littéral `$classname$` est remplacé par le nom de la classe englobante à cet emplacement dans le fichier de code.

```xml
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
            <Code Language="csharp" Format="CData">
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

## <a name="simpletypename-example"></a>Exemple de SimpleTypeName

Cet exemple montre comment utiliser la fonction `SimpleTypeName`. Quand cet extrait de code est inséré dans un fichier de code, le littéral `$SystemConsole$` est remplacé par la forme la plus simple du type <xref:System.Console> dans le contexte dans lequel l’extrait de code a été appelé.

```xml
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

- [Function, élément](../ide/code-snippets-schema-reference.md#function-element)
- [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md)
