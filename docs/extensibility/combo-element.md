---
title: Élément combo | Microsoft Docs
description: 'L’élément combo définit les commandes qui s’affichent dans une zone de liste déroulante. Il existe quatre types : DropDownCombo, DynamicCombo, IndexCombo et MRUCombo.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904953"
---
# <a name="combo-element"></a>Élément combo
Définit les commandes qui s’affichent dans une zone de liste déroulante. Il existe quatre types de zones de liste déroulante, comme suit : DropDownCombo, DynamicCombo, IndexCombo et MRUCombo.

## <a name="syntax"></a>Syntaxe

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|guid|Obligatoire. GUID de l’identificateur de la commande GUID/ID.|
|id|Obligatoire. ID de l’identificateur de la commande GUID/ID.|
|defaultWidth|Obligatoire. Entier qui spécifie une largeur en pixels pour la zone de liste déroulante.|
|idCommandList|Obligatoire. ID qui est envoyé à la cible de commande active pour récupérer la liste des éléments à afficher dans la zone de liste déroulante. L’ID sera dans la même portée GUID que le contrôle.|
|priority|Optionnel. Valeur numérique qui spécifie la priorité.|
|type|Optionnel. Valeur énumérée qui spécifie le type de bouton.<br /><br /> S’il n’est pas spécifié, utilise le bouton.<br /><br /> DropDownCombo<br /> Le VSPackage est chargé de remplir le contenu de cette zone de liste déroulante. L’utilisateur ne peut pas taper quoi que ce soit dans la zone de texte de cette liste déroulante.<br /><br /> DynamicCombo<br /> Le VSPackage est chargé de remplir le contenu de cette zone de liste déroulante. L’utilisateur peut modifier cette liste déroulante et également sélectionner des éléments.<br /><br /> IndexCombo<br /> Identique à DynamicCombo, sauf qu’il déclenche l’index de l’élément plutôt que son texte.<br /><br /> MRUCombo<br /> Rempli par l’environnement de développement intégré (IDE) pour le compte du VSPackage.  L’utilisateur peut modifier cette zone de liste déroulante. L’IDE se souvient des 16 dernières entrées par zone de liste déroulante.<br /><br /> Lorsque l’utilisateur sélectionne un nom dans la zone de liste déroulante ou entre un nouveau, l’IDE notifie le VSPackage approprié.|
|Condition|Optionnel. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|Optionnel. Élément parent du bouton.|
|CommandFlag|Obligatoire. Consultez [élément indicateur de commande](../extensibility/command-flag-element.md). Les valeurs CommandFlag valides pour un bouton sont les suivantes.<br /><br /> -CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> -Touches filtres<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> -Nocustom<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Chaînes|Obligatoire. Consultez l' [élément Strings](../extensibility/strings-element.md). L’élément ButtonText enfant doit être défini.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d’outils VSPackage.|

## <a name="example"></a>Exemple

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Voir aussi
- [Fichiers de table de commandes Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
