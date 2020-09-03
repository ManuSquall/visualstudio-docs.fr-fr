---
title: '&lt;&gt;Élément RelatedProducts (programme d’amorçage) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202540"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Élément RelatedProducts (programme d’amorçage)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `RelatedProducts` élément définit d’autres produits qui dépendent de ou qui sont inclus dans le produit actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant spécifie que Microsoft installer est installé avec le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et, par conséquent, n’a pas besoin d’une installation distincte.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<Product> Appartient](../deployment/product-element-bootstrapper.md)
