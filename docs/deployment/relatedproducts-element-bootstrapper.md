---
title: "&lt;RelatedProducts&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> (élément du programme d'amorçage)"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;RelatedProducts&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément `RelatedProducts` définit d'autres produits qui dépendent ou sont inclus dans le produit actuel.  
  
## Syntaxe  
  
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
  
## Éléments et attributs  
 L'élément `RelatedProducts` est un enfant de l'élément `Product`.  Il ne possède aucun attribut.  
  
## DependsOnProduct  
 L'élément `DependsOnProduct` signifie que le produit actuel dépend du produit nommé et que le produit nommé doit être installé avant le produit actuel.  Il représente un enfant de l'élément `RelatedProducts`.  Un élément `RelatedProducts` peut contenir un ou plusieurs éléments `DependsOnProduct`.  
  
 `DependsOnProduct` possède l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Code`|Nom de code du produit inclus, tel qu'il est spécifié par l'attribut `ProductCode` de l'élément `Product`.  Pour plus d'informations, consultez [\<Product\>, élément](../deployment/product-element-bootstrapper.md).|  
  
## EitherProducts  
 L'élément `EitherProducts` définit zéro, un ou plusieurs éléments `DependsOnProduct` et n'a pas d'attributs.  Au moins un `DependsOnProduct` dans ce jeu doit être installé avant le produit actuel.  Un élément `RelatedProducts` peut contenir zéro, un ou plusieurs éléments `EitherProducts`.  
  
## IncludesProduct  
 L'élément `IncludesProduct` signifie qu'un produit est inclus avec l'installation actuelle et ne requiert pas d'installation distincte.  Il représente un enfant de l'élément `RelatedProducts`.  Un élément `RelatedProducts` peut contenir un ou plusieurs éléments `IncludesProduct`.  
  
 `IncludesProduct` possède l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Code`|Nom de code du produit inclus, tel qu'il est spécifié par l'attribut `ProductCode` de l'élément `Product`.  Pour plus d'informations, consultez [\<Product\>, élément](../deployment/product-element-bootstrapper.md).|  
  
## Exemple  
 L'exemple de code suivant spécifie que Microsoft Installer est installé avec le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] et, par conséquent, qu'aucune installation distincte n'est nécessaire.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## Voir aussi  
 [\<Product\>, élément](../deployment/product-element-bootstrapper.md)