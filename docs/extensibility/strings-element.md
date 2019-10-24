---
title: Élément Strings | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719442"
---
# <a name="strings-element"></a>Élément Strings
L’élément Strings doit contenir au moins un élément enfant **ButtonText** . Tous les autres éléments enfants sont facultatifs. Les caractères XML non valides tels que' & 'et' < 'doivent être codés en tant qu’entités ('&amp;'et'&lt;', etc.).

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
|language|Optionnel. Language = ".".|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|ButtonText|Ce champ et les cinq champs de texte suivants dans une définition de commande vous permettent de spécifier le texte qui apparaît dans différents menus. Par défaut, le champ `ButtonText` s’affiche dans les contrôleurs de menu. Le champ `ButtonText` devient également la valeur par défaut si les autres champs de texte sont vides. Le champ `ButtonText` ne peut pas être vide, même si les autres champs de texte sont spécifiés.|
|ToolTipText|Le champ `ToolTipText` spécifie le texte qui apparaît dans l’info-bulle pour un élément de menu.<br /><br /> Si le champ `ToolTipText` est vide, le champ `ButtonText` est utilisé.|
|MenuText|Le champ `MenuText` spécifie le texte affiché pour une commande s’il se trouve dans le menu principal, dans une barre d’outils, dans un menu contextuel ou dans un sous-menu. Si le champ `MenuText` est vide, l’environnement de développement intégré (IDE) utilise le champ `ButtonText`. Le champ `MenuText` peut également être utilisé pour la localisation.<br /><br /> Pour les menus contextuels, le champ `MenuText` est le nom qui s’affiche dans la barre d’outils menus contextuels, qui permet la personnalisation des menus contextuels dans l’IDE. Par conséquent, soyez précis dans le nom de votre menu contextuel. par exemple, utilisez « menu contextuel de package de widgets » au lieu de « raccourci ».<br /><br /> Si le champ `MenuText` n’est pas spécifié, le champ `ButtonText` est utilisé.|
|CommandName|Le champ `CommandName` spécifie le texte qui apparaît dans la catégorie clavier sous l’onglet **commandes** de la boîte de dialogue **personnaliser** (disponible en cliquant sur **personnaliser** dans le menu **Outils** ).|
|CanonicalName|Le champ `CanonicalName` anglais spécifie le nom de la commande dans le texte anglais qui peut être entré dans la fenêtre de **commande** pour exécuter l’élément de menu. L’IDE supprime tous les caractères qui ne sont pas des lettres, des chiffres, des traits de soulignement ou des points incorporés. Ce texte est ensuite concaténé dans le champ `ButtonText` pour définir la commande. Par exemple, **nouveau projet** dans le menu **fichier** devient la commande, file. NewProject.<br /><br /> Si le champ `CanonicalName` anglais n’est pas spécifié, l’IDE utilise le champ `ButtonText` et supprime tous les caractères sauf les lettres, les chiffres, les traits de soulignement et les points incorporés. Par exemple, le texte du bouton « & définir des commandes... » devient DefineCommands, où l’esperluette, l’espace et les points de suspension sont supprimés.<br /><br /> Si l’indicateur de `TextChanges` est spécifié et que le texte de la commande est modifié, la commande correspondante reconnue par la fenêtre de **commande** ne change pas. Il reste la forme canonique des champs d’origine du `ButtonText` ou de l’anglais `CanonicalName`.|
|LocCanonicalName|Le champ `LocCanonicalName` se comporte de la même façon que le champ English `CanonicalName`, mais permet de spécifier le texte de commande localisé. Les deux champs canoniques peuvent être spécifiés. Étant donné que l’IDE analyse simplement le texte entré dans la fenêtre **commande** et l’associe à une commande, il est possible d’associer à la fois l’anglais et du texte non anglais à la même commande.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Button](../extensibility/button-element.md)|Définit un élément avec lequel l’utilisateur peut interagir.|
|[Élément Menu](../extensibility/menu-element.md)|Définit un élément de menu unique.|
|[Élément Combo](../extensibility/combo-element.md)|Définit les commandes qui s’affichent dans une zone de liste déroulante.|

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)