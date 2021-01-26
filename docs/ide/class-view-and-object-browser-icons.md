---
title: Affichage de classes et Explorateur d'objets, icônes
description: En savoir plus sur les Affichage de classes et l’Explorateur d’objets affichent les icônes qui représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e0348c1f6c51f0a82328814be671d8f44e3d4a7
ms.sourcegitcommit: 3922edfe67063e1ede418cdbf6aa6293117c4855
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98773348"
---
# <a name="class-view-and-object-browser-icons"></a>Icônes Affichage de classes et Explorateur d’objets

L’**affichage de classes** et l’**Explorateur d’objets** affichent des icônes qui représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables. Le tableau suivant illustre et décrit ces icônes.

|Icône|Description|Icône|Description|
|----------|-----------------|----------|-----------------|
|![Symbole d'espace de noms](../ide/media/vxnamespace_icon.gif)|Espace de noms|![Symbole de déclaration](../ide/media/vxmethod_icon.gif)|Méthode ou fonction|
|![Icône de classe](../ide/media/vxclass_icon.gif)|Classe|![Symbole d'opérateur](../ide/media/vxoperator_icon.gif)|Opérateur|
|![Symbole d'interface Lollipop](../ide/media/vxinterface_icon.gif)|Interface|![Symbole de la propriété](../ide/media/vxproperty_icon.gif)|Propriété|
|![Symbole de la structure](../ide/media/vxstruct_icon.gif)|Structure|![Icône de champ](../ide/media/vxfield_icon.gif)|Champ ou variable|
|![Symbole Union](../ide/media/vxunion_icon.gif)|Union|![Symbole d'événement](../ide/media/vxevent_icon.gif)|Événement|
|![Symbole d'énumération](../ide/media/vxenum_icon.gif)|Énumération|![Icône de constante](../ide/media/vxconstant_icon.gif)|Constante|
|![Symbole de définition du type](../ide/media/vxtypedef_icon.gif)|TypeDef|![Symbole d'élément d'énumération](../ide/media/vxenumitem_icon.gif)|Élément enum|
|![Symbole du module Visual Studio](../ide/media/vxmodule_icon.gif)|Module|![Symbole d'élément de carte](../ide/media/vxmapitem_icon.gif)|Élément Map|
|![Symbole de méthode d'extension](../ide/media/extensionmethod.gif)|Méthode d’extension|![Symbole de déclaration](../ide/media/vxmethod_icon.gif)|Déclaration externe|
|![Symbole de délégué](../ide/media/vxdelegate_icon.gif)|Délégué|![Icône d'erreur pour l'affichage de classes et l'explorateur d'objets](../ide/media/erroricon.gif)|Error|
|![Symbole d'exception](../ide/media/vxexception_icon.gif)|Exception|![Symbole du modèle](../ide/media/vxtemplate_icon.gif)|Modèle|
|![Symbole de carte](../ide/media/vxmap_icon.gif)|Mappage|![Symbole de point d'exclamation d'erreur](../ide/media/vxerror_icon.gif)|Unknown|
|![Symbole de transfert de type](../ide/media/ob_type_forward.gif)|Transfert de type|||

> [!TIP]
> Pour afficher au mieux les icônes de cette page, assurez-vous que votre thème de Microsoft Docs est défini sur **clair**. Vous pouvez basculer ce thème de couleur à partir du contrôle situé en bas à gauche de la page, comme indiqué dans la capture d’écran suivante :
>
> ![Thème docs](../ide/media/toggle-docs-color-theme.png "Activer/désactiver le thème de couleur pour les pages Microsoft Docs")

## <a name="signal-icons"></a>Icônes de signalisation

Les icônes de signalisation suivantes s’appliquent à toutes les icônes précédentes et indiquent leur accessibilité.

|Icône|Description|
|----------|-----------------|
|\<No Signal Icon>|Public. Accessible à partir de n’importe où dans le composant et à partir de tout composant qui y fait référence.|
|![Symbole Signal protégé](../ide/media/vxsignal_icon_key.gif)|Protégée. Accessible à partir de la classe ou le type conteneur, ou à partir de celles ou ceux dérivés de la classe ou du type conteneur.|
|![Symbole Signal privé](../ide/media/vxsignal_icon_lock.gif)|Privé. Accessible uniquement dans la classe ou le type conteneur.|
|![Symbole Signal Sealed](../ide/media/vxsignal_icon_envelope.gif)|Sealed.|
|![Symbole Signal Friend&#47;interne](../ide/media/vxsignal_icon_diamond.gif)|Friend/interne. Accessible uniquement à partir du projet.|
|![Flèche d'icône de signalisation](../ide/media/vxsignal_icon_arrow.gif)|Raccourci. Raccourci vers l’objet.|

> [!NOTE]
> Si votre projet est inclus dans une base de données contenant le contrôle de code source, des icônes de signalisation supplémentaires peuvent s’afficher pour indiquer l’état du contrôle de code source (par exemple, archivé ou extrait).

> [!TIP]
> Pour afficher d’autres images d’application et icônes qui apparaissent dans Visual Studio, téléchargez la [**bibliothèque d’images Visual Studio**](https://www.microsoft.com/download/details.aspx?id=35825).

## <a name="see-also"></a>Voir aussi

- [Affichage de la structure du code](../ide/viewing-the-structure-of-code.md)
