---
title: Affichage de classes et Explorateur d'objets, icônes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44b86f079feceebf00bb1a39adcf3ab84622474d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="class-view-and-object-browser-icons"></a>Icônes Affichage de classes et Explorateur d’objets

L’**affichage de classes** et l’**Explorateur d’objets** affichent des icônes qui représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables. Le tableau suivant illustre et décrit ces icônes.

|Icône|Description|Icône|Description|
|----------|-----------------|----------|-----------------|
|![Symbole d’espace de noms](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|Espace de noms|![Symbole de déclaration](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Méthode ou fonction|
|![Icône de classe](../ide/media/vxclass_icon.gif "vxClass_Icon")|Classe|![Symbole d’opérateur](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Opérateur|
|![Symbole d’interface Lollipop](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Interface|![Symbole de propriété](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|Propriété|
|![Symbole de structure](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Structure|![Icône de champ](../ide/media/vxfield_icon.gif "vxField_Icon")|Champ ou variable|
|![Symbole Union](../ide/media/vxunion_icon.gif "vxUnion_Icon")|Union|![Symbole d’événement](../ide/media/vxevent_icon.gif "vxEvent_Icon")|événement|
|![Symbole d’énumération](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Icône de constante](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Constante|
|![Symbole de définition du type](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Symbole d’élément d’énumération](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Élément enum|
|![Symbole du module Visual Studio](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Module|![Symbole d’élément de carte](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Élément Map|
|![Symbole de méthode d’extension](../ide/media/extensionmethod.gif "ExtensionMethod")|Méthode d’extension|![Symbole de déclaration](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Déclaration externe|
|![Symbole de délégué](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|délégué|![Icône d’erreur pour l’affichage de classes et l’Explorateur d’objets ](../ide/media/erroricon.gif "ErrorIcon")|Error|
|![Symbole d’exception](../ide/media/vxexception_icon.gif "vxException_Icon")|Exception|![Symbole de modèle](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Modèle|
|![Symbole de carte](../ide/media/vxmap_icon.gif "vxMap_Icon")|Carte|![Symbole de point d’exclamation d’erreur](../ide/media/vxerror_icon.gif "vxError_Icon")|Inconnu|
|![Symbole de transfert de type](../ide/media/ob_type_forward.gif "ob_type_forward")|Transfert de type|||

## <a name="signal-icons"></a>Icônes de signalisation

Les icônes de signalisation suivantes s’appliquent à toutes les icônes précédentes et indiquent leur accessibilité.

|Icône|Description|
|----------|-----------------|
|\<Aucune icône de signalisation>|Publique. Accessible à partir de n’importe où dans le composant et à partir de tout composant qui y fait référence.|
|![Symbole Signal protégé](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Protégée. Accessible à partir de la classe ou le type conteneur, ou à partir de celles ou ceux dérivés de la classe ou du type conteneur.|
|![Symbole Signal privé](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Privée. Accessible uniquement dans la classe ou le type conteneur.|
|![Symbole Signal Sealed](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Sealed.|
|![Signal Friend&#47;Symbole interne](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Friend/interne. Accessible uniquement à partir du projet.|
|![Flèche d’icône de signalisation](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Raccourci. Raccourci vers l’objet.|

> [!NOTE]
> Si votre projet est inclus dans une base de données contenant le contrôle de code source, des icônes de signalisation supplémentaires peuvent s’afficher pour indiquer l’état du contrôle de code source (par exemple, archivé ou extrait).

## <a name="see-also"></a>Voir aussi

- [Afficher la structure du code](../ide/viewing-the-structure-of-code.md)