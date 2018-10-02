---
title: '&lt;signature&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b6172609b68e1800dd71b9367d93a52596e88cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492823"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Documentation Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Regroupe un ensemble d’éléments connexes pour une fonction ou une méthode pour fournir une documentation pour les fonctions surchargées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Paramètres  
 `externalid`  
 Facultatif. Si le `format` d’attribut pour le [ \<loc >](../ide/loc-javascript.md) élément est `vsdoc`, cet attribut spécifie l’ID utilisé pour localiser le code XML qui est associé à la signature de membre. Contrairement à la `locid` attribut, cet attribut spécifie que tous les éléments dans le membre qui possède cet ID doivent être chargés. Les informations de description associé contenues dans le code XML sont également fusionnées avec les éléments spécifiés dans la signature. Cela vous permet de spécifier des éléments supplémentaires, tels que `<capability>`, dans le fichier side-car sans les spécifier dans le fichier source. `externalid` est un attribut facultatif.  
  
 `externalFile`  
 Facultatif. Spécifie le nom du fichier dans lequel rechercher le `externalid`. Cet attribut est ignoré si aucun `externalid` est présent. Il s’agit d’un attribut facultatif. La valeur par défaut est le nom du fichier actif mais avec une extension de fichier de .xml au lieu de .js. Par défaut, les règles de recherche de ressources managé pour la localisation sont utilisés pour rechercher le fichier.  
  
 `helpKeyword`  
 Facultatif. Le mot clé d’aide F1.  
  
 `locid`  
 Facultatif. L’identificateur pour les informations de localisation sur le champ. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) balise.  
  
## <a name="remarks"></a>Notes  
 Utilisez une `<signature>` élément pour chaque surchargé description de la fonction dans le fichier .js, ou utilisez un `<signature>` élément pour chaque ID de membre externe spécifié.  
  
 Le `<signature>` élément doit être placé dans le corps de fonction avant les instructions. Lorsque vous utilisez [ \<Résumé >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), ou [ \<retourne >](../ide/returns-javascript.md) éléments avec le `<signature>` élément, Placez les autres éléments à l’intérieur de la `<signature>` bloc.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le `<signature>` élément.  
  
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



