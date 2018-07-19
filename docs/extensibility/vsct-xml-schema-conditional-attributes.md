---
title: Attributs conditionnels du schéma XML de VSCT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975ca2f5fa6f070baf07b26cbfa0d8c3aa3b67d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138354"
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