---
title: Attributs conditionnels du schéma XML VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ee3d25fd7d08ea52c41ef24fdfe654bbf7a2eb2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246873"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributs conditionnels du schéma XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Attributs conditionnels peuvent être appliqués à tous les éléments et les listes. Opérateurs logiques et les expressions d’expansion symbole équivalente à true ou false. Si la valeur est true, la liste associée ou l’élément est inclus dans la sortie résultante.  
  
 Extensions de jeton peuvent être testées par rapport à d’autres extensions de jeton ou des constantes. La fonction Defined() est utilisée pour tester si un nom particulier a été défini, même si elle n’a aucune valeur.  
  
 Lorsqu’un attribut Condition est appliqué à une liste, la condition est appliquée à chaque élément enfant dans la liste. Si un élément enfant lui-même contient un attribut de Condition, sa condition est combinée avec l’expression parent par une opération AND.  
  
 Les valeurs 1, « 1 » et « trues » sont évaluées comme true et 0, '0' et 'false' sont évaluées comme false.  
  
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
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

