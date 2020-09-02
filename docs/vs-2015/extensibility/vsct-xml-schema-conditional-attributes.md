---
title: Attributs conditionnels de schéma XML VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422147"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributs conditionnels du schéma XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les attributs conditionnels peuvent être appliqués à toutes les listes et éléments. Les opérateurs logiques et les expressions d’expansion de symboles prennent la valeur true ou false. Si la valeur est true, la liste ou l’élément associé est inclus dans la sortie obtenue.  
  
 Les expansions de jeton peuvent être testées par rapport à d’autres constantes ou expansions de jeton. La fonction définie () permet de tester si un nom particulier a été défini, même s’il n’a pas de valeur.  
  
 Lorsqu’un attribut condition est appliqué à une liste, la condition est appliquée à chaque élément enfant de la liste. Si un élément enfant lui-même contient un attribut condition, sa condition est combinée avec l’expression parente par une opération AND.  
  
 Les valeurs 1, « 1 » et « true » sont évaluées comme vraies, et 0, « 0 » et « false » sont évalués comme faux.  
  
## <a name="operators"></a>Opérateurs  
 Les opérateurs suivants peuvent être utilisés pour évaluer des expressions conditionnelles.  
  
|Opérateur|Définition|  
|--------------|----------------|  
|(,)|Regroupement|  
|!|Opérateur NOT logique|  
|\<, >, \<=, >=, ==, !=|Opérateurs relationnels et opérateurs d'égalité|  
|et|Boolean|  
|ou|Boolean|  
  
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
