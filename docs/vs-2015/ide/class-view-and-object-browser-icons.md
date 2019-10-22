---
title: Affichage de classes et Explorateur d’objets, icônes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620481"
---
# <a name="class-view-and-object-browser-icons"></a>Affichage de classes et Explorateur d'objets, icônes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’Affichage de classes** et l’**Explorateur d’objets** affichent des icônes qui représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables. Le tableau suivant illustre et décrit ces icônes.

|Icône|Description|Icône|Description|
|----------|-----------------|----------|-----------------|
|![Symbole d’espace de noms](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Espace de noms|![Symbole de déclaration](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Méthode ou fonction|
|![Icône de classe](../ide/media/vxclass-icon.gif "vxClass_Icon")|Class|![Symbole d’opérateur](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|opérateur|
|![Symbole d’interface Lollipop](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interface|![Symbole de la propriété](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Property|
|![Symbole de structure](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Structure|![Icône de champ](../ide/media/vxfield-icon.gif "vxField_Icon")|Champ ou variable|
|![Symbole d’Union](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![Symbole d’événement](../ide/media/vxevent-icon.gif "vxEvent_Icon")|événement|
|![Symbole d’énumération](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Icône constante](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Constante|
|![Symbole de définition de type](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Symbole d’élément d’énumération](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Élément enum|
|![Symbole du module Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Module|![Symbole d’élément cartographique](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Élément Map|
|![Symbole de méthode d’extension](../ide/media/extensionmethod.gif "ExtensionMethod")|Méthode d'extension|![Symbole de déclaration](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Déclaration externe|
|![Symbole délégué](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|délégué|![Icône d’erreur pour Affichage de classes et l’Explorateur d’objets](../ide/media/erroricon.gif "ErrorIcon")|Erreur|
|![Symbole d’exception](../ide/media/vxexception-icon.gif "vxException_Icon")|Exception|![Symbole de modèle](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Modèle|
|![Symbole de la carte](../ide/media/vxmap-icon.gif "vxMap_Icon")|Carte|![Symbole du point d’exclamation d’erreur](../ide/media/vxerror-icon.gif "vxError_Icon")|Inconnu|
|![Symbole de transfert de type](../ide/media/ob-type-forward.gif "ob_type_forward")|Transfert de type|||

## <a name="signal-icons"></a>icônes de signalisation
 Les icônes de signalisation suivantes s’appliquent à toutes les icônes précédentes et indiquent leur accessibilité.

> [!NOTE]
> Si votre projet est inclus dans une base de données contenant le contrôle de code source, des icônes de signalisation supplémentaires peuvent s’afficher pour indiquer l’état du contrôle de code source (par exemple, archivé ou extrait).

|Icône|Description|
|----------|-----------------|
|\<Aucune icône de signalisation>|Publique. Accessible à partir de n’importe où dans le composant et à partir de tout composant qui y fait référence.|
|![Symbole de signal protégé](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Protégée. Accessible à partir de la classe ou le type conteneur, ou à partir de celles ou ceux dérivés de la classe ou du type conteneur.|
|![Symbole privé de signal](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privée. Accessible uniquement dans la classe ou le type conteneur.|
|![Symbole de signal sealed](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Sealed.|
|![Symbole de&#47;signal Friend Internal](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/interne. Accessible uniquement à partir du projet.|
|![Flèche d’icône de signal](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Raccourci. Raccourci vers l’objet.|

## <a name="see-also"></a>Voir aussi
 [Affichage de la structure du code](../ide/viewing-the-structure-of-code.md)
