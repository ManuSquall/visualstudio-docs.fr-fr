---
title: ATTRIBUTs conditionnels VSCT XML Schema (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697948"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>ATTRIBUTs conditionnels du schéma VSCT XML
Vous pouvez appliquer des attributs conditionnels à toutes les listes et articles. Les opérateurs logiques et les expressions d’expansion des symboles s’évaluent à la réalité ou au faux. Si c’est vrai, la liste ou l’élément associé est inclus dans la sortie résultante.

 Vous pouvez tester les expansions de jetons contre d’autres expansions ou constantes symboliques. La `Defined()` fonction teste si un nom particulier a été défini, même s’il n’a aucune valeur.

 Lorsqu’un attribut de condition est appliqué à une liste, la condition est appliquée à chaque élément enfant de la liste. Si un élément enfant lui-même contient un attribut de condition, alors son état est combiné avec l’expression parent par une opération ET.

 Les valeurs 1, '1' et 'vraies' sont évaluées comme vraies, et 0, '0' et 'faux' sont évalués comme faux.

## <a name="operators"></a>Opérateurs
 Utilisez les opérateurs suivants pour évaluer les expressions conditionnelles.

|Opérateur|Définition|
|--------------|----------------|
|(,)|Regroupement|
|!|Opérateur NOT logique|
|\<, >, \<>, ', !'|Opérateurs relationnels et opérateurs d'égalité|
|and|Boolean|
|or|Boolean|

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
- [Table de commande Visual Studio (. Vsct) fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
