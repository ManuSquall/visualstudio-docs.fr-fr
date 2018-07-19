---
title: '&lt;RelatedProducts&gt; élément (programme d’amorçage) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c541a9775025183a3b3ffbf21ef5b72c3f00cc87
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077801"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; élément (programme d’amorçage)
Le `RelatedProducts` élément définit d’autres produits qui dépendent ou sont inclus dans le produit actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le `RelatedProducts` élément est un enfant de le `Product` élément. Il a pas d’attributs.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 Le `DependsOnProduct` élément signifie que le produit actuel varie selon le produit nommé et que le produit nommé doit être installé avant l’actuel. C’est un enfant de le `RelatedProducts` élément. Un `RelatedProducts` élément peut avoir un ou plusieurs `DependsOnProduct` éléments.  
  
 `DependsOnProduct` a l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Code`|Le nom de code du produit inclus, tel que spécifié par le `ProductCode` attribut de la `Product` élément. Pour plus d’informations, consultez [ \<produit > élément](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Le `EitherProducts` élément définit zéro ou plusieurs `DependsOnProduct` éléments, et n’a aucun attribut. Au moins un `DependsOnProduct` dans ce jeu doit être installé avant le produit actuel. Un `RelatedProducts` élément peut avoir zéro ou plusieurs `EitherProducts` éléments.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Le `IncludesProduct` élément signifie qu’un produit est inclus avec l’installation actuelle et ne nécessite pas d’une installation distincte. C’est un enfant de le `RelatedProducts` élément. Un `RelatedProducts` élément peut avoir un ou plusieurs `IncludesProduct` éléments.  
  
 `IncludesProduct` a l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Code`|Le nom de code du produit inclus, tel que spécifié par le `ProductCode` attribut de la `Product` élément. Pour plus d’informations, consultez [ \<produit > élément](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant spécifie que Microsoft Installer est installé avec le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]et donc qu’une installation distincte n’est nécessaire.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<Produit > élément](../deployment/product-element-bootstrapper.md)