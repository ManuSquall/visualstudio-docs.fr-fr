---
title: '&lt;&gt;Élément RelatedProducts (programme d’amorçage) | Microsoft Docs'
description: L’élément RelatedProducts définit d’autres produits qui dépendent de ou sont inclus dans le produit actuel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ac9f84fa22526ed03d7a2e9b201cc9afc2f476d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350567"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Élément RelatedProducts (programme d’amorçage)
L' `RelatedProducts` élément définit d’autres produits qui dépendent de ou qui sont inclus dans le produit actuel.

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
 L' `RelatedProducts` élément est un enfant de l' `Product` élément. Elle n’a pas d’attribut.

## <a name="dependsonproduct"></a>DependsOnProduct
 L' `DependsOnProduct` élément signifie que le produit actuel dépend du produit nommé et que le produit nommé doit être installé avant le produit actuel. Il s’agit d’un enfant de l' `RelatedProducts` élément. Un `RelatedProducts` élément peut avoir un ou plusieurs `DependsOnProduct` éléments.

 `DependsOnProduct` a l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`Code`|Nom de code du produit inclus, tel que spécifié par l' `ProductCode` attribut de l' `Product` élément. Pour plus d’informations, consultez [ \<Product> élément](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 L' `EitherProducts` élément définit zéro, un ou plusieurs `DependsOnProduct` éléments et n’a pas d’attributs. Au moins un `DependsOnProduct` objet de ce groupe doit être installé avant le produit actuel. Un `RelatedProducts` élément peut avoir zéro, un ou plusieurs `EitherProducts` éléments.

## <a name="includesproduct"></a>IncludesProduct
 L' `IncludesProduct` élément signifie qu’un produit est inclus dans l’installation actuelle et ne nécessite pas d’installation distincte. Il s’agit d’un enfant de l' `RelatedProducts` élément. Un `RelatedProducts` élément peut avoir un ou plusieurs `IncludesProduct` éléments.

 `IncludesProduct` a l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`Code`|Nom de code du produit inclus, tel que spécifié par l' `ProductCode` attribut de l' `Product` élément. Pour plus d’informations, consultez [ \<Product> élément](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a> Exemple
 L’exemple de code suivant spécifie que Microsoft installer est installé avec le .NET Framework et, par conséquent, n’a pas besoin d’une installation distincte.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Voir aussi
- [\<Product> appartient](../deployment/product-element-bootstrapper.md)