---
title: "Affichage de classes et Explorateur d&#39;objets, ic&#244;nes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "icônes, dans l’Explorateur d’objets"
  - "icônes de signalisation"
  - "Affichage de classes (outil), symboles"
  - "symboles graphiques"
  - "IntelliSense, icônes"
  - "icônes, IntelliSense"
  - "symboles, icônes de l’Explorateur d’objets"
  - "Explorateur d’objets, icônes de la fenêtre Affichage de classes"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Affichage de classes et Explorateur d&#39;objets, ic&#244;nes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les icônes **Affichage de classes** et **Explorateur d'objets** représentent des entités de code, par exemple, des espaces de noms, des classes, des fonctions et des variables.  Le tableau suivant illustre et décrit les icônes.  
  
|Icône|Description|Icône|Description|  
|-----------|-----------------|-----------|-----------------|  
|![Symbole d'espace de noms](~/docs/ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|Espace de noms|![Symbole de déclaration](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Méthode ou fonction|  
|![Icône de classe](~/docs/ide/media/vxclass_icon.gif "vxClass\_Icon")|Classe|![Symbole d'opérateur](~/docs/ide/media/vxoperator_icon.gif "vxOperator\_Icon")|Opérateur|  
|![Symbole d'interface Lollipop](~/docs/ide/media/vxinterface_icon.gif "vxInterface\_Icon")|Interface|![Symbole de la propriété](~/docs/ide/media/vxproperty_icon.gif "vxProperty\_Icon")|Property|  
|![Symbole de la structure](~/docs/ide/media/vxstruct_icon.gif "vxStruct\_Icon")|Structure|![Icône de champ](~/docs/ide/media/vxfield_icon.gif "vxField\_Icon")|Champ ou variable|  
|![Symbole Union](~/docs/ide/media/vxunion_icon.gif "vxUnion\_Icon")|Union|![Symbole d'événement](~/docs/ide/media/vxevent_icon.gif "vxEvent\_Icon")|Événement|  
|![Symbole d'énumération](~/docs/ide/media/vxenum_icon.gif "vxEnum\_Icon")|Enum|![Icône de constante](~/docs/ide/media/vxconstant_icon.gif "vxConstant\_Icon")|Constante|  
|![Symbole de définition du type](~/docs/ide/media/vxtypedef_icon.gif "vxTypeDef\_Icon")|TypeDef|![Symbole d'élément d'énumération](~/docs/ide/media/vxenumitem_icon.gif "vxEnumItem\_Icon")|Élément enum|  
|![Symbole du module Visual Studio](~/docs/ide/media/vxmodule_icon.gif "vxModule\_Icon")|Module|![Symbole d'élément de carte](~/docs/ide/media/vxmapitem_icon.gif "vxMapItem\_Icon")|Élément map|  
|![Symbole de méthode d'extension](~/docs/ide/media/extensionmethod.gif "ExtensionMethod")|Méthode d'extension|![Symbole de déclaration](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Déclaration externe|  
|![Symbole de délégué](~/docs/ide/media/vxdelegate_icon.gif "vxDelegate\_Icon")|Délégué|![Icône d'erreur pour l'affichage de classes et l'explorateur d'objets](~/docs/ide/media/erroricon.gif "ErrorIcon")|Erreur|  
|![Symbole d'exception](~/docs/ide/media/vxexception_icon.gif "vxException\_Icon")|Exception|![Symbole du modèle](~/docs/ide/media/vxtemplate_icon.gif "vxTemplate\_Icon")|Modèle|  
|![Symbole de carte](~/docs/ide/media/vxmap_icon.gif "vxMap\_Icon")|Table|![Symbole de point d'exclamation d'erreur](~/docs/ide/media/vxerror_icon.gif "vxError\_Icon")|Inconnu|  
|![Symbole de transfert de type](~/docs/ide/media/ob_type_forward.gif "ob\_type\_forward")|Transfert de type|||  
  
## Icônes de signalisation  
 Les icônes de signalisation suivantes s'appliquent à toutes les icônes précédentes et indiquent leur accessibilité.  
  
> [!NOTE]
>  Si votre projet est inclus dans une base de données contenant le contrôle de code source, des icônes de signal supplémentaires peuvent s'afficher pour indiquer l'état du symbole \(extrait, par exemple\).  
  
|Icône|Description|  
|-----------|-----------------|  
|\<Aucune icône de signalisation\>|Public.  Accessible depuis n'importe quel endroit du composant et depuis tout composant qui y fait référence.|  
|![Symbole Signal protégé](~/docs/ide/media/vxsignal_icon_key.gif "vxSignal\_Icon\_Key")|Protégée.  Accessible depuis la classe ou le type conteneur, ou depuis celles ou ceux dérivés de la classe ou du type conteneur.|  
|![Symbole Signal privé](~/docs/ide/media/vxsignal_icon_lock.gif "vxSignal\_Icon\_Lock")|Privée.  Accessible uniquement dans la classe ou le type conteneur.|  
|![Symbole Signal Sealed](~/docs/ide/media/vxsignal_icon_envelope.gif "vxSignal\_Icon\_Envelope")|Sealed.|  
|![Signal Friend&#47;Symbole interne](~/docs/ide/media/vxsignal_icon_diamond.gif "vxSignal\_Icon\_Diamond")|Ami\/interne.  Accessible uniquement depuis le projet.|  
|![Flèche d'icône de signalisation](~/docs/ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|Raccourci.  Raccourci vers l'objet.|  
  
## Voir aussi  
 [Affichage de la structure du code](../ide/viewing-the-structure-of-code.md)