---
title: '&lt;loc&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651480"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie l’emplacement et le type du fichier side-car qui fournit des informations IntelliSense localisées.

## <a name="syntax"></a>Syntaxe

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Paramètres
 `filename` Facultatif. Nom racine du fichier side-car qui contient les informations de localisation pour la culture neutre. Lorsque Visual Studio recherche des informations de localisation, il tente de trouver une version spécifique à la culture de ce fichier. Par exemple, si `filename` est jquery.xml, Visual Studio recherche le dossier correct propre à la culture (par exemple, ja) au même emplacement que le fichier. js qui contient l' `<loc>` élément. S’il localise le dossier propre à la culture, il vérifie s’il existe un fichier de jquery.xml. S’il ne parvient pas à localiser le fichier approprié, il utilise à la place des règles d’emplacement de ressources managées. La valeur par défaut de `filename` est le nom du fichier actif, mais avec une extension. xml au lieu de. js.

 `format` Facultatif. Type de fichier side-car utilisé pour la localisation. Utilisez `messagebundle` pour spécifier l’utilisation des groupes de messages définis par les métadonnées Ajax ouvertes. `messagebundle` est le format recommandé. Toutefois, ce format n’est pas pris en charge dans les fichiers Microsoft Ajax ou. winmd. Utilisez `vsdoc` pour spécifier le format de localisation .NET Framework standard utilisé par Microsoft Ajax et Windows Runtime. Cet attribut est facultatif. `vsdoc` est le format par défaut.

## <a name="remarks"></a>Notes
 L' `<loc>` élément doit apparaître en haut du fichier dans la même section que l' `<reference>` élément. Les règles d’utilisation de l' `<loc>` élément sont les mêmes que celles de l' `<reference>` élément. Pour plus d’informations, consultez la section « directives de références » dans [JavaScript IntelliSense](../ide/javascript-intellisense.md).

 Visual Studio traite un `<loc>` élément unique pour chaque fichier. js. Si plusieurs `<loc>` éléments sont présents, un seul `<loc>` élément est utilisé. Le comportement pour déterminer l' `<loc>` élément à utiliser n’est pas défini.

 Lorsque vous utilisez le format de groupement de messages, utilisez l' `locid` attribut dans les commentaires de documentation XML pour spécifier la valeur de l' `name` attribut.

## <a name="example"></a>Exemple
 L’exemple suivant montre comment utiliser l' `<loc>` élément avec le format messagebundle. Ajoutez le code XML suivant à un fichier nommé messageFilename.xml et placez le fichier dans le dossier propre à la culture, comme indiqué dans la description du `filename` paramètre.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Pour l’exemple messagebundle, ajoutez le code suivant à un fichier JavaScript dans votre projet. L' `<loc>` élément doit apparaître en tant que première ligne dans le fichier JavaScript. Les descriptions de ce code seront remplacées par des descriptions localisées, si elles sont disponibles.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 L’exemple suivant utilise le format VSDoc. Ajoutez le code XML suivant à un fichier nommé scriptFilename.xml et placez le fichier dans le dossier propre à la culture.

```
<?xml version="1.0" encoding="utf-8" ?>
<doc>
  <assembly>
    <name>Lights</name>
  </assembly>
  <members>
    <member name="M:illuminate">
      <summary>Activates a light. </summary>
      <param name='a'>The light to activate. </param>
    </member>
  </members>
</doc>

```

 Pour l’exemple VSDoc, ajoutez le code suivant à un fichier JavaScript dans votre projet. Les descriptions de ce code seront remplacées par des descriptions localisées, si elles sont disponibles.

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>Voir aussi
 [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md)
