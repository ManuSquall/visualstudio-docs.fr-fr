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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cb80c7ad81708724750660560d65cfef722af86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785047"
---
# <a name="class-view-and-object-browser-icons"></a>Affichage de classes et Explorateur d'objets, icônes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’**affichage de classes** et l’Explorateur d’objets affichent des icônes qui représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables. Le tableau suivant illustre et décrit ces icônes.  
  
|Icône|Description|Icône|Description|  
|----------|-----------------|----------|-----------------|  
|![Symbole d’espace de noms](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Espace de noms|![Symbole de déclaration](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Méthode ou fonction|  
|![Icône de classe](../ide/media/vxclass-icon.gif "vxClass_Icon")|Classe|![Symbole d’opérateur](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Opérateur|  
|![Symbole d’interface Lollipop](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interface|![Symbole de propriété](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Property|  
|![Symbole de structure](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Structure|![Icône de champ](../ide/media/vxfield-icon.gif "vxField_Icon")|Champ ou variable|  
|![Symbole Union](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![Symbole d’événement](../ide/media/vxevent-icon.gif "vxEvent_Icon")|événement|  
|![Symbole d’énumération](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Icône de constante](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Constante|  
|![Symbole de définition du type](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Symbole d’élément d’énumération](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Élément enum|  
|![Symbole du module Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Module|![Symbole d’élément de carte](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Élément Map|  
|![Symbole de méthode d’extension](../ide/media/extensionmethod.gif "ExtensionMethod")|Méthode d'extension|![Symbole de déclaration](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Déclaration externe|  
|![Symbole de délégué](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|délégué|![Icône d’erreur pour l’affichage de classes et l’Explorateur d’objets ](../ide/media/erroricon.gif "ErrorIcon")|Error|  
|![Symbole d’exception](../ide/media/vxexception-icon.gif "vxException_Icon")|Exception|![Symbole de modèle](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Modèle|  
|![Symbole de carte](../ide/media/vxmap-icon.gif "vxMap_Icon")|Carte|![Symbole de point d’exclamation d’erreur](../ide/media/vxerror-icon.gif "vxError_Icon")|Inconnu|  
|![Symbole de transfert de type](../ide/media/ob-type-forward.gif "ob_type_forward")|Transfert de type|||  
  
## <a name="signal-icons"></a>icônes de signalisation  
 Les icônes de signalisation suivantes s’appliquent à toutes les icônes précédentes et indiquent leur accessibilité.  
  
> [!NOTE]
>  Si votre projet est inclus dans une base de données contenant le contrôle de code source, des icônes de signalisation supplémentaires peuvent s’afficher pour indiquer l’état du contrôle de code source (par exemple, archivé ou extrait).  
  
|Icône|Description|  
|----------|-----------------|  
|\<Aucune icône de signalisation>|Publique. Accessible à partir de n’importe où dans le composant et à partir de tout composant qui y fait référence.|  
|![Symbole Signal protégé](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Protégée. Accessible à partir de la classe ou le type conteneur, ou à partir de celles ou ceux dérivés de la classe ou du type conteneur.|  
|![Symbole Signal privé](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privée. Accessible uniquement dans la classe ou le type conteneur.|  
|![Symbole Signal Sealed](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Sealed.|  
|![Signal Friend&#47;Symbole interne](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/interne. Accessible uniquement à partir du projet.|  
|![Flèche d’icône de signalisation](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Raccourci. Raccourci vers l’objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage de la structure du code](../ide/viewing-the-structure-of-code.md)
