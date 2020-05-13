---
title: Élément Combo ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739818"
---
# <a name="combo-element"></a>Élément Combo
Définit les commandes qui apparaissent dans une boîte combo. Il existe quatre types de boîtes combo, comme suit: DropDownCombo, DynamicCombo, IndexCombo, et MRUCombo.

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
|guid|Obligatoire. GUID de l’identifiant de commande GUID/ID.|
|id|Obligatoire. ID de l’identifiant de commande GUID/ID.|
|defaultWidth|Obligatoire. Un intégrant qui spécifie une largeur de pixel pour la boîte combo.|
|idCommandList|Obligatoire. Une pièce d’identité envoyée à la cible de commande active pour récupérer la liste des éléments à afficher dans la boîte de combo. L’ID sera dans la même portée GUID que le contrôle.|
|priority|facultatif. Une valeur numérique qui spécifie la priorité.|
|type|facultatif. Une valeur énumérée qui spécifie le type de bouton.<br /><br /> Si elle n’est pas donnée, utilise Button.<br /><br /> DropDownCombo (en)<br /> Le VSPackage est responsable du remplissage du contenu de cette boîte combo. L’utilisateur ne peut rien taper dans la boîte de texte de cette chute.<br /><br /> DynamicCombo (en)<br /> Le VSPackage est responsable du remplissage du contenu de cette boîte combo. L’utilisateur peut modifier ce combo et également sélectionner des éléments en elle.<br /><br /> IndexCombo (en)<br /> La même chose que DynamicCombo sauf qu’il soulève l’index de l’élément plutôt que son texte.<br /><br /> MRUCombo (en)<br /> Rempli par l’environnement de développement intégré (IDE) pour le compte de la VSPackage.  L’utilisateur peut modifier dans cette boîte combo. L’IDE se souvient jusqu’aux 16 dernières entrées par boîte combo.<br /><br /> Lorsque l’utilisateur sélectionne quelque chose dans la boîte combo, ou entre quelque chose de nouveau, l’IDE informe le VSPackage approprié.|
|Condition|facultatif. Voir [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|Parent|facultatif. L’élément parent du bouton.|
|CommandFlag (commandFlag)|Obligatoire. Voir [l’élément drapeau du Commandement](../extensibility/command-flag-element.md). Les valeurs commandflag valides pour un bouton sont les suivantes.<br /><br /> - CasSensible<br /><br /> - CommandWellOnly<br /><br /> - DéfautDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibilité<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Chaînes|Obligatoire. Voir [l’élément Cordes](../extensibility/strings-element.md). L’élément ButtonText de l’enfant doit être défini.|
|Annotation|Commentaire facultatif.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[Élément de commande](../extensibility/commands-element.md)|Représente la collection de commandes sur la barre d’outils VSPackage.|

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
- [Fichiers visualister de table de commande de studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
