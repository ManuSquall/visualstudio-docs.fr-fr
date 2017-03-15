---
title: "&lt;loc&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<loc>, balise XML JavaScript"
  - "loc, balise XML JavaScript"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie l'emplacement et le type du fichier annexe qui fournit des informations localisées IntelliSense.  
  
## Syntaxe  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### Paramètres  
 `filename`  
 Optionnel.  Le nom racine du fichier annexe qui contient les informations de localisation pour la culture neutre.  Lorsque Visual Studio recherche les informations de localisation, il essaie de trouver une version de ce fichier culturellement spécifique.  Par exemple, si `filename` est jquery.xml, recherche Visual Studio pour le dossier approprié culturellement spécifique \(comme JA\) dans le même emplacement que le fichier .js qui contient l'élément `<loc>`.  S'il trouve le dossier culturellement spécifique, il vérifie si un fichier de jquery.xml existe dans celui\-ci.  S'il ne trouve pas le fichier correct, il utilise à la place des règles de gestion des ressources de position.  La valeur par défaut pour `filename` est le nom du fichier actif, mais avec une extension .xml au lieu .js.  
  
 `format`  
 Optionnel.  Type de fichier annexe utilisé pour la localisation.  Utilisez `messagebundle` pour spécifier l'utilisation des paquets de messages définis par les métadonnées Open Ajax.  `messagebundle` est le format recommandé.  Toutefois, ce format n'est pas pris en charge dans Microsoft Ajax ou dans les fichiers de .winmd.  Utilisez `vsdoc` pour spécifier le format de localisation du .NET Framework standard utilisé par Microsoft Ajax et Windows Runtime.  Cet attribut est facultatif.  `vsdoc` est le format par défaut.  
  
## Notes  
 L'élément `<loc>` doit apparaître au début du fichier dans la même section que l'élément `<reference>`.  Les règles d'utilisation pour l'élément `<loc>` sont différents de l'élément `<reference>`.  Pour plus d'informations, consultez la section « Références Directives » dans [IntelliSense JavaScript](../ide/javascript-intellisense.md).  
  
 Visual Studio traite un élément `<loc>` unique pour chaque fichier .js.  Si plusieurs éléments `<loc>` sont présents, un unique élément `<loc>` est utilisé.  Comportement pour déterminer quel élément`<loc>` utiliser s'il n'est pas défini.  
  
 Lorsque vous utilisez le format de pack de message, utilisez l'attribut `locid` dans les commentaires de documentation XML pour spécifier la valeur d'attribut `name`.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'élément `<loc>` avec format messagebundle.  Ajoutez le XML suivant dans un fichier nommé messageFilename.xml et placez le fichier dans le dossier approprié culturellement spécifique, comme spécifié dans la description du paramètre `filename`.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Pour l'exemple de messagebundle, ajoutez le code suivant dans un fichier JavaScript dans votre projet.  L'élément `<loc>` doit apparaître comme première ligne du fichier JavaScript.  Les descriptions dans ce code seront remplacées par les descriptions localisées, si disponibles.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 L'exemple suivant utilise le format de VSDoc.  Ajoutez le XML suivant dans un fichier nommé scriptFilename.xml et placez le fichier dans le dossier approprié culturellement spécifique.  
  
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
  
 Pour l'exemple de VSDoc, ajoutez le code suivant dans un fichier JavaScript dans votre projet.  Les descriptions dans ce code seront remplacées par les descriptions localisées, si disponibles.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)