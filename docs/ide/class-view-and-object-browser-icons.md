---
title: Affichage de classes et Explorateur d'objets, icônes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 29d39c210a14934ba50ace92692bee944b6b75c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844390"
---
# <a name="class-view-and-object-browser-icons"></a>Icônes Affichage de classes et Explorateur d’objets

L’**affichage de classes** et l’**Explorateur d’objets** affichent des icônes qui représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables. Le tableau suivant illustre et décrit ces icônes.

|Icône|Description|Icône|Description|
|----------|-----------------|----------|-----------------|
|![Symbole d'espace de noms](../ide/media/vxnamespace_icon.gif)|Espace de noms|![Symbole de déclaration](../ide/media/vxmethod_icon.gif)|Méthode ou fonction|
|![Icône de classe](../ide/media/vxclass_icon.gif)|Classe|![Symbole d'opérateur](../ide/media/vxoperator_icon.gif)|Opérateur|
|![Symbole d'interface Lollipop](../ide/media/vxinterface_icon.gif)|Interface|![Symbole de la propriété](../ide/media/vxproperty_icon.gif)|Property|
|![Symbole de la structure](../ide/media/vxstruct_icon.gif)|Structure|![Icône de champ](../ide/media/vxfield_icon.gif)|Champ ou variable|
|![Symbole Union](../ide/media/vxunion_icon.gif)|Union|![Symbole d'événement](../ide/media/vxevent_icon.gif)|événement|
|![Symbole d'énumération](../ide/media/vxenum_icon.gif)|Enum|![Icône de constante](../ide/media/vxconstant_icon.gif)|Constante|
|![Symbole de définition du type](../ide/media/vxtypedef_icon.gif)|TypeDef|![Symbole d'élément d'énumération](../ide/media/vxenumitem_icon.gif)|Élément enum|
|![Symbole du module Visual Studio](../ide/media/vxmodule_icon.gif)|Module|![Symbole d'élément de carte](../ide/media/vxmapitem_icon.gif)|Élément Map|
|![Symbole de méthode d’extension](../ide/media/extensionmethod.gif)|Méthode d’extension|![Symbole de déclaration](../ide/media/vxmethod_icon.gif)|Déclaration externe|
|![Symbole de délégué](../ide/media/vxdelegate_icon.gif)|délégué|![Icône d'erreur pour l'affichage de classes et l'explorateur d'objets](../ide/media/erroricon.gif)|Error|
|![Symbole d'exception](../ide/media/vxexception_icon.gif)|Exception|![Symbole du modèle](../ide/media/vxtemplate_icon.gif)|Modèle|
|![Symbole de carte](../ide/media/vxmap_icon.gif)|Carte|![Symbole de point d'exclamation d'erreur](../ide/media/vxerror_icon.gif)|Inconnu|
|![Symbole de transfert de type](../ide/media/ob_type_forward.gif)|Transfert de type|||

## <a name="signal-icons"></a>Icônes de signalisation

Les icônes de signalisation suivantes s’appliquent à toutes les icônes précédentes et indiquent leur accessibilité.

|Icône|Description|
|----------|-----------------|
|\<Aucune icône de signalisation>|Publique. Accessible à partir de n’importe où dans le composant et à partir de tout composant qui y fait référence.|
|![Symbole Signal protégé](../ide/media/vxsignal_icon_key.gif)|Protégée. Accessible à partir de la classe ou le type conteneur, ou à partir de celles ou ceux dérivés de la classe ou du type conteneur.|
|![Symbole Signal privé](../ide/media/vxsignal_icon_lock.gif)|Privée. Accessible uniquement dans la classe ou le type conteneur.|
|![Symbole Signal Sealed](../ide/media/vxsignal_icon_envelope.gif)|Sealed.|
|![Symbole Signal Friend&#47;interne](../ide/media/vxsignal_icon_diamond.gif)|Friend/interne. Accessible uniquement à partir du projet.|
|![Flèche d'icône de signalisation](../ide/media/vxsignal_icon_arrow.gif)|Raccourci. Raccourci vers l’objet.|

> [!NOTE]
> Si votre projet est inclus dans une base de données contenant le contrôle de code source, des icônes de signalisation supplémentaires peuvent s’afficher pour indiquer l’état du contrôle de code source (par exemple, archivé ou extrait).

## <a name="see-also"></a>Voir aussi

- [Afficher la structure du code](../ide/viewing-the-structure-of-code.md)