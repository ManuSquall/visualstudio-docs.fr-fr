---
title: Élément Strings | Microsoft Docs
description: L’élément Strings contient un élément enfant ButtonText et d’autres éléments enfants facultatifs. Une esperluette dans la chaîne de texte spécifie un raccourci clavier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899405"
---
# <a name="strings-element"></a>Élément Strings
L’élément Strings doit contenir au moins un élément enfant **ButtonText** . Tous les autres éléments enfants sont facultatifs. Les caractères XML non valides tels que' & 'et' < 'doivent être codés en tant qu’entités (' &amp; 'et' &lt; ', etc.).

 Une esperluette dans la chaîne de texte spécifie le raccourci clavier de la commande.

## <a name="syntax"></a>Syntaxe

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|langage|Optionnel. Language = ".".|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|ButtonText|Ce champ et les cinq champs de texte suivants dans une définition de commande vous permettent de spécifier le texte qui apparaît dans différents menus. Par défaut, le `ButtonText` champ apparaît dans les contrôleurs de menu. Le `ButtonText` champ devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` champ ne peut pas être vide même si les autres champs de texte sont spécifiés.|
|ToolTipText|Le `ToolTipText` champ spécifie le texte qui apparaît dans l’info-bulle pour un élément de menu.<br /><br /> Si le `ToolTipText` champ est vide, le `ButtonText` champ est utilisé.|
|MenuText|Le `MenuText` champ spécifie le texte affiché pour une commande s’il se trouve dans le menu principal, dans une barre d’outils, dans un menu contextuel ou dans un sous-menu. Si le `MenuText` champ est vide, l’environnement de développement intégré (IDE) utilise le `ButtonText` champ. Le `MenuText` champ peut également être utilisé pour la localisation.<br /><br /> Pour les menus contextuels, le `MenuText` champ est le nom qui s’affiche dans la barre d’outils menus contextuels, qui permet la personnalisation des menus contextuels dans l’IDE. Par conséquent, soyez précis dans le nom de votre menu contextuel. par exemple, utilisez « menu contextuel de package de widgets » au lieu de « raccourci ».<br /><br /> Si le `MenuText` champ n’est pas spécifié, le `ButtonText` champ est utilisé.|
|CommandName|Le `CommandName` champ spécifie le texte qui apparaît dans la catégorie clavier sous l’onglet **commandes** de la boîte de dialogue **personnaliser** (disponible en cliquant sur **personnaliser** dans le menu **Outils** ).|
|CanonicalName|Le `CanonicalName` champ anglais spécifie le nom de la commande dans le texte anglais qui peut être entré dans la fenêtre de **commande** pour exécuter l’élément de menu. L’IDE supprime tous les caractères qui ne sont pas des lettres, des chiffres, des traits de soulignement ou des points incorporés. Ce texte est ensuite concaténé dans le `ButtonText` champ pour définir la commande. Par exemple, **nouveau projet** dans le menu **fichier** devient la commande, file. NewProject.<br /><br /> Si le `CanonicalName` champ anglais n’est pas spécifié, l’IDE utilise le `ButtonText` champ et supprime tous les caractères sauf les lettres, les chiffres, les traits de soulignement et les points incorporés. Par exemple, le texte du bouton « &définir des commandes... » devient DefineCommands, où l’esperluette, l’espace et les points de suspension sont supprimés.<br /><br /> Si l' `TextChanges` indicateur est spécifié et que le texte de la commande est modifié, la commande correspondante reconnue par la fenêtre de **commande** ne change pas ; elle reste la forme canonique des `ButtonText` champs d’origine ou anglais `CanonicalName` .|
|LocCanonicalName|Le `LocCanonicalName` champ se comporte de la même façon que le `CanonicalName` champ anglais, mais il permet de spécifier le texte de commande localisé. Les deux champs canoniques peuvent être spécifiés. Étant donné que l’IDE analyse simplement le texte entré dans la fenêtre **commande** et l’associe à une commande, il est possible d’associer à la fois l’anglais et du texte non anglais à la même commande.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Button](../extensibility/button-element.md)|Définit un élément avec lequel l’utilisateur peut interagir.|
|[Élément Menu](../extensibility/menu-element.md)|Définit un élément de menu unique.|
|[Élément Combo](../extensibility/combo-element.md)|Définit les commandes qui s’affichent dans une zone de liste déroulante.|

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
