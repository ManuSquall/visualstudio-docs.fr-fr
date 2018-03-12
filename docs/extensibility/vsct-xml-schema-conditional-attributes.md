---
title: "Attributs conditionnels du schéma XML de VSCT | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75b593110f68cd559717ae87920e898f39cdeb43
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributs conditionnels du schéma XML de VSCT
Attributs conditionnels peuvent être appliqués à tous les éléments et les listes. Opérateurs logiques et les expressions d’expansion de symbole équivalente à true ou false. Si la valeur est true, la liste associée ou l’élément est inclus dans le résultat.  
  
 Extensions de jeton peuvent être testées par rapport à d’autres extensions de jeton ou des constantes. La fonction Defined() est utilisée pour tester si un nom particulier a été défini, même si elle n’a aucune valeur.  
  
 Lorsqu’un attribut Condition est appliqué à une liste, la condition est appliquée à chaque élément enfant dans la liste. Si un élément enfant elle-même contient un attribut Condition, puis sa condition est associée à l’expression parent par une opération AND.  
  
 Les valeurs 1, '1' et 'trues' sont évaluées comme true et 0, '0' et 'false' sont évaluées comme false.  
  
## <a name="operators"></a>Opérateurs  
 Les opérateurs suivants peuvent être utilisés pour évaluer des expressions conditionnelles.  
  
|Opérateur|Définition|  
|--------------|----------------|  
|(,)|Regroupement|  
|!|Opérateur NOT logique|  
|\<, >, \<=, >=, ==, !=|Opérateurs relationnels et opérateurs d'égalité|  
|et|Booléen|  
|ou|Booléen|  
  
## <a name="examples"></a>Exemples  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)