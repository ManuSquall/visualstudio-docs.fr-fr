---
title: Attributs conditionnels de schéma XML VSCT | Microsoft Docs
description: Découvrez comment appliquer des attributs conditionnels à des listes et éléments de schéma XML VSCT. Les attributs ont la valeur true ou false, contrôlant la sortie obtenue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e91207016ed6e1baab80b323680d10a40e0331d8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905252"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributs conditionnels du schéma XML VSCT
Vous pouvez appliquer des attributs conditionnels à toutes les listes et éléments. Les opérateurs logiques et les expressions d’expansion de symboles prennent la valeur true ou false. Si la valeur est true, la liste ou l’élément associé est inclus dans la sortie obtenue.

 Vous pouvez tester les expansions de jeton par rapport à d’autres constantes ou expansions de jeton. La fonction `Defined()` teste si un nom particulier a été défini, même s’il n’a pas de valeur.

 Lorsqu’un attribut condition est appliqué à une liste, la condition est appliquée à chaque élément enfant de la liste. Si un élément enfant lui-même contient un attribut condition, sa condition est combinée avec l’expression parente par une opération AND.

 Les valeurs 1, « 1 » et « true » sont évaluées comme vraies, et 0, « 0 » et « false » sont évalués comme faux.

## <a name="operators"></a>Opérateurs
 Utilisez les opérateurs suivants pour évaluer des expressions conditionnelles.

|Opérateur|Définition|
|--------------|----------------|
|(,)|Regroupement|
|!|Opérateur NOT logique|
|\<, >, \<=, >=, ==, !=|Opérateurs relationnels et opérateurs d'égalité|
|et|Boolean|
|ou|Boolean|

## <a name="examples"></a>Exemples

```xml
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
- [Table de commandes Visual Studio (. Fichiers vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
