---
title: '&lt;loc&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9314453b5e75e31f98d6989efa274278706bc5a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244008"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie l’emplacement et le type de fichier side-car qui fournit des informations IntelliSense localisées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 Facultatif. Le nom de la racine du fichier side-car qui contient des informations de localisation pour la culture neutre. Lorsque Visual Studio recherche les informations de localisation, il tente de trouver une version spécifique à la culture de ce fichier. Par exemple, si `filename` est jquery.xml, Visual Studio recherche le dossier spécifique à la culture approprié (par exemple, JA) dans le même emplacement que le fichier .js qui contient le `<loc>` élément. Si il localise le dossier spécifique à la culture, il vérifie l’existence d’un fichier jquery.xml qu’il contient. Si elle ne peut pas localiser le fichier approprié, il utilise à la place des règles d’emplacement de ressources gérées. La valeur par défaut `filename` est le nom du fichier actuel, mais avec une extension .xml au lieu de .js.  
  
 `format`  
 Facultatif. Le type de fichier side-car utilisé pour la localisation. Utiliser `messagebundle` pour spécifier l’utilisation de regroupements de message défini par les métadonnées Ajax ouvert. `messagebundle` est le format recommandé. Toutefois, ce format n’est pas pris en charge dans Microsoft Ajax ou dans les fichiers .winmd. Utilisez `vsdoc` pour spécifier le format de localisation .NET Framework standard qui est utilisé par Microsoft Ajax et Windows Runtime. Cet attribut est facultatif. `vsdoc` est le format par défaut.  
  
## <a name="remarks"></a>Notes  
 Le `<loc>` élément doit apparaître en haut du fichier dans la même section que le `<reference>` élément. L’utilisation des règles pour le `<loc>` élément sont les mêmes que les `<reference>` élément. Pour plus d’informations, consultez la section « Références Directives » dans [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
 Visual Studio traite un seul `<loc>` élément pour chaque fichier .js. Si plusieurs `<loc>` éléments sont présents, qu’un seul `<loc>` élément est utilisé. Comportement pour déterminer les `<loc>` élément à utiliser n’est pas défini.  
  
 Lorsque vous utilisez le format d’offre groupée de message, utilisez la `locid` attribut dans les commentaires de documentation XML pour spécifier le `name` valeur d’attribut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `<loc>` élément messagebundle format. Ajoutez le code XML suivant dans un fichier nommé messageFilename.xml et placez le fichier dans le dossier spécifique à la culture approprié, tel que spécifié dans la description de le `filename` paramètre.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Pour l’exemple messagebundle, ajoutez le code suivant dans un fichier JavaScript dans votre projet. Le `<loc>` élément doit apparaître en tant que la première ligne dans le fichier JavaScript. Les descriptions de ce code seront remplacées par des descriptions localisées, s’il est disponible.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 L’exemple suivant utilise le format de VSDoc. Ajoutez le code XML suivant dans un fichier nommé scriptFilename.xml et placez le fichier dans le dossier approprié de la culture spécifique.  
  
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
  
 Pour l’exemple VSDoc, ajoutez le code suivant dans un fichier JavaScript dans votre projet. Les descriptions de ce code seront remplacées par des descriptions localisées, s’il est disponible.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)



