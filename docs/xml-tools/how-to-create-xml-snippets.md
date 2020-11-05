---
title: 'Procédure : créer des extraits XML'
description: Découvrez comment utiliser l’éditeur XML dans Visual Studio pour créer des extraits XML qui vous permettent de créer des fichiers XML plus rapidement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d935f479e3133db8fb5340359d6a354058a3020a
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400028"
---
# <a name="how-to-create-xml-snippets"></a>Comment : créer des extraits XML

L’éditeur XML peut être utilisé pour créer des extraits XML. Cet éditeur comporte un extrait XML appelé « Snippet », qui est souvent utilisé pour la création de nouveaux extraits XML.

## <a name="to-create-a-new-xml-snippet"></a>Pour créer un nouvel extrait XML

Pour créer un nouvel extrait de code XML, créez un nouveau fichier XML et utilisez la fonctionnalité **Insérer un extrait** .

1. Dans le menu **fichier** , cliquez sur **nouveau** , puis sur **fichier**.

2. Cliquez sur **fichier XML** , puis sur **ouvrir**.

3. Cliquez avec le bouton droit dans le volet de l’éditeur et sélectionnez **Insérer un extrait**.

4. Sélectionnez **Snippet** dans la liste et appuyez sur **entrée**.

5. Apportez les modifications voulues au nouvel extrait.

6. Dans le menu **fichier** , sélectionnez **Enregistrer XMLFile.xml**.

     La boîte de dialogue **enregistrer le fichier sous** s’affiche.

7. Entrez le nom du nouvel extrait et sélectionnez **fichiers d’extraits** de code dans la fenêtre déroulante **type de fichier** .

8. Utilisez la liste déroulante **enregistrer dans** pour remplacer l’emplacement du fichier par *Mes documents\Visual Studio 2005 \ code Snippets\XML\My XML Snippets* , puis appuyez sur **Enregistrer**.

## <a name="snippet-description"></a>Description de l’extrait

Cette section décrit certains éléments clés de l'extrait souvent utilisé. Pour plus d’informations sur les éléments de schéma utilisés par les extraits XML, consultez [référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType, élément

L'éditeur prend en charge deux types d'extraits :

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Le `Expansion` type détermine si l’extrait apparaît lorsque vous appelez la commande **Insérer un extrait** . Le `SurroundsWith` type détermine si l’extrait apparaît lorsque vous appelez la commande **entourer de** .

### <a name="code-element"></a>Élément de code

L'élément `Code` définit le texte XML qui sera inséré lorsque l'extrait sera appelé.

> [!NOTE]
> Le texte de l'extrait XML doit être placé dans une section `<![CDATA[...]]>`.

L'élément `Code` suivant est créé par l'extrait souvent utilisé.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

L'élément `Code` inclut trois variables.

- $name$ est une variable définie par l'utilisateur. Elle crée un élément `name` dont la valeur par défaut modifiable est « name ». Les variables définies par l'utilisateur se définissent à l'aide de l'élément `Literal`.

- $selected$ est une variable prédéfinie. Il représente le texte qui a été sélectionné dans l’éditeur XML avant l’appel de l’extrait de code. La position de cette variable détermine l'emplacement du texte sélectionné dans l'extrait de code qui entoure cette sélection.

- $end$ est une variable prédéfinie. Quand l’utilisateur appuie sur **entrée** pour terminer la modification des champs de l’extrait de code, cette variable détermine l’emplacement où le signe insertion (^) est déplacé.

  L'élément `Code` ci-dessus insère le texte XML suivant :

```xml
<test>
  <name>name</name>
</test>
```

La valeur de l'élément name est marquée comme une zone modifiable.

### <a name="literal-element"></a>Literal, élément

L'élément `Literal` permet d'identifier le texte de remplacement qui peut être personnalisé après son insertion dans le fichier. Par exemple, des chaînes littérales, des valeurs numériques et certains noms de variables peuvent être déclarés comme littéraux. Vous pouvez définir un nombre quelconque de littéraux dans votre extrait XML et y faire référence plusieurs fois dans l'extrait. L'exemple d'élément `Literal` suivant définit une variable $name$ dont la valeur par défaut est « name ».

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Les littéraux peuvent également faire référence à des fonctions. L’éditeur XML comprend une fonction nommée **LookupPrefix**. La fonction **LookupPrefix** recherche l’URI d’espace de noms donné à partir de l’emplacement dans le document XML à partir duquel cet extrait de code est appelé et retourne le préfixe d’espace de noms défini pour cet espace de noms, le cas échéant, et il comprend le signe deux-points ( :) dans ce nom. L’exemple suivant illustre un `Literal` élément qui utilise la fonction **LookupPrefix** .

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

La variable $prefix$ _peut alors être utilisée ailleurs dans votre extrait XML.

## <a name="see-also"></a>Voir aussi

- [extraits XML](../xml-tools/xml-snippets.md)
- [Comment : utiliser des extraits XML](../xml-tools/how-to-use-xml-snippets.md)
- [Comment : générer un extrait XML à partir d’un schéma XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
