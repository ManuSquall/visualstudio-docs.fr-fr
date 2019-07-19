---
title: '&lt;signature&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02a4c36f3969ca0f9ef61e817afb82eb8247f041
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203482"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regroupe un ensemble d’éléments connexes pour une fonction ou une méthode pour fournir une documentation pour les fonctions surchargées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Paramètres  
 `externalid`  
 facultatif. Si le `format` d’attribut pour le [ \<loc >](../ide/loc-javascript.md) élément est `vsdoc`, cet attribut spécifie l’ID utilisé pour localiser le code XML qui est associé à la signature de membre. Contrairement à la `locid` attribut, cet attribut spécifie que tous les éléments dans le membre qui possède cet ID doivent être chargés. Les informations de description associé contenues dans le code XML sont également fusionnées avec les éléments spécifiés dans la signature. Cela vous permet de spécifier des éléments supplémentaires, tels que `<capability>`, dans le fichier side-car sans les spécifier dans le fichier source. `externalid` est un attribut facultatif.  
  
 `externalFile`  
 facultatif. Spécifie le nom du fichier dans lequel rechercher le `externalid`. Cet attribut est ignoré si aucun `externalid` est présent. Il s’agit d’un attribut facultatif. La valeur par défaut est le nom du fichier actif mais avec une extension de fichier de .xml au lieu de .js. Par défaut, les règles de recherche de ressources managé pour la localisation sont utilisés pour rechercher le fichier.  
  
 `helpKeyword`  
 facultatif. Mot clé pour l’aide F1.  
  
 `locid`  
 facultatif. L’identificateur pour les informations de localisation sur le champ. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans la balise [\<loc>](../ide/loc-javascript.md).  
  
## <a name="remarks"></a>Remarques  
 Utilisez une `<signature>` élément pour chaque surchargé description de la fonction dans le fichier .js, ou utilisez un `<signature>` élément pour chaque ID de membre externe spécifié.  
  
 Le `<signature>` élément doit être placé dans le corps de fonction avant les instructions. Lorsque vous utilisez [ \<Résumé >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), ou [ \<retourne >](../ide/returns-javascript.md) éléments avec le `<signature>` élément, Placez les autres éléments à l’intérieur de la `<signature>` bloc.  
  
## <a name="example"></a>Exemples  
 L’exemple de code suivant montre comment utiliser l'élément `<signature>`.  
  
```javascript  
// Use of <signature> with externalid.  
// Requires use of the <loc> tag to identify the external functions.  
function illuminate(light) {  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>  
    ///   <param name='light' type='Number' />  
    /// </signature>  
}  
  
// Use of <signature> for overloads implemented in JavaScript.  
function add(a, b) {  
    /// <signature>  
    /// <summary>function summary 1</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 2 – differ by number of params</summary>  
    /// <param name="a" type="Number">Only 1 parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 3 – differ by parameter type</summary>  
    /// <param name="a" type="Number">Number parameter</param>  
    /// <param name="b" type="String">String parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 4 – differ by return type</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="String" />  
    /// </signature>  
  
    return a + b;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)
