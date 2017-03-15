---
title: "Attributs conditionnels du sch&#233;ma XML de VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, attributs conditionnels"
  - "attributs conditionnels (schéma XML de VSCT)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Attributs conditionnels du sch&#233;ma XML de VSCT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Attributs conditionnels peuvent être appliqués à toutes les listes et les éléments. Opérateurs logiques et les expressions d'expansion symbole équivalente à true ou false. Si la valeur est true, la liste associée ou l'élément est inclus dans le résultat.  
  
 Extensions de jeton peuvent être testées par rapport à d'autres extensions de jeton ou des constantes. La fonction Defined\(\) est utilisée pour tester si un nom particulier a été défini, même si elle n'a aucune valeur.  
  
 Lorsqu'un attribut Condition est appliqué à une liste, la condition est appliquée à chaque élément enfant dans la liste. Si un élément enfant lui\-même contient un attribut Condition, son état est combiné avec l'expression parent par une opération AND.  
  
 Les valeurs 1, « 1 » et « trues » sont évaluées comme true et 0, « 0 » et « false » sont considérées comme false.  
  
## Opérateurs  
 Les opérateurs suivants peuvent être utilisés pour évaluer les expressions conditionnelles.  
  
|Opérateur|Définition|  
|---------------|----------------|  
|\(,\)|Regroupement|  
|\!|Opérateur NOT logique|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|Relationnels et d'égalité|  
|et|Booléen|  
|ou|Booléen|  
  
## Exemples  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)