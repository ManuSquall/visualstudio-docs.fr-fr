---
title: Élément de cordes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699730"
---
# <a name="strings-element"></a>Élément Strings
L’élément Cordes doit contenir au moins un élément **d’enfant ButtonText.** Tous les autres éléments pour enfants sont facultatifs. Les caractères XML invalides tels que «&» et «<» doivent être&amp;codés&lt;en tant qu’entités (« et » et « et ainsi de suite).

 Un ampersand dans la chaîne de texte spécifie le raccourci clavier pour la commande.

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
|langage|facultatif. Langue "."|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|BoutonTexte|Ce champ et les cinq champs de texte suivants dans une définition de commande vous permettent de spécifier le texte qui apparaît dans différents menus. Par défaut, `ButtonText` le champ apparaît dans les contrôleurs de menu. Le `ButtonText` champ devient également le défaut si les autres champs de texte sont vides. Le `ButtonText` champ ne peut pas être vide même si les autres champs de texte sont spécifiés.|
|ToolTipText|Le `ToolTipText` champ spécifie le texte qui apparaît dans la pointe d’outil pour un élément de menu.<br /><br /> Si `ToolTipText` le champ est `ButtonText` vide, le champ est utilisé.|
|MenuTexte|Le `MenuText` champ spécifie le texte qui est affiché pour une commande s’il est sur le menu principal, une barre d’outils, dans un menu raccourci, ou dans un sous-mois. Si `MenuText` le champ est vide, l’environnement de `ButtonText` développement intégré (IDE) utilise le champ. Le `MenuText` champ peut également être utilisé pour la localisation.<br /><br /> Pour les menus `MenuText` raccourcis, le champ est le nom qui est affiché dans la barre d’outils Shortcut Menus, qui permet la personnalisation des menus de raccourci dans l’IDE. Par conséquent, être précis dans ce que vous nommez votre menu raccourci; par exemple, utilisez "Widget Package Shortcut Menu" au lieu de "Shortcut".<br /><br /> Si `MenuText` le champ n’est pas spécifié, le `ButtonText` champ est utilisé.|
|CommandName|Le `CommandName` champ spécifie le texte qui apparaît dans la catégorie clavier dans **l’onglet Commandes** dans la boîte de dialogue **Customize** (disponible en cliquant sur **Personnaliser** sur le menu **Outils).**|
|CanonicalName (en)|Le `CanonicalName` champ anglais spécifie le nom de la commande en texte anglais qui peut être entré dans la fenêtre **de commande** pour exécuter l’élément du menu. L’IDE dépouille tous les caractères qui ne sont pas des lettres, des chiffres, des souligne ou des périodes intégrées. Ce texte est ensuite concaté sur le `ButtonText` terrain pour définir la commande. Par exemple, **New Project** sur le menu **Du fichier** devient la commande, File.NewProject.<br /><br /> Si le `CanonicalName` champ anglais n’est pas `ButtonText` spécifié, l’IDE utilise le champ, et dépouille tous sauf les lettres, les chiffres, les souligne et les périodes intégrées. Par exemple, le texte bouton "&Définir les commandes..." devient DefineCommands, où l’ampersand, l’espace et l’ellipsis sont supprimés.<br /><br /> Si `TextChanges` le drapeau est spécifié et que le texte de la commande est modifié, la commande correspondante reconnue par la fenêtre **du Commandement** ne change pas; il reste la forme canonique des champs d’origine `ButtonText` ou d’anglais. `CanonicalName`|
|LocCanonicalName|Le `LocCanonicalName` champ se comporte de `CanonicalName` la même manière que le champ anglais, mais permet de préciser le texte de commande localisé. Les deux champs canoniques peuvent être spécifiés. Étant donné que l’IDE analyse simplement le texte entré dans la fenêtre **du Commandement** et l’associe à une commande, le texte anglais et non anglais peut être associé à la même commande.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Button](../extensibility/button-element.md)|Définit un élément avec lequel l’utilisateur peut interagir.|
|[Élément Menu](../extensibility/menu-element.md)|Définit un seul élément de menu.|
|[Élément Combo](../extensibility/combo-element.md)|Définit les commandes qui apparaissent dans une boîte combo.|

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
