---
title: "Interfaces de fournisseur de symboles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces, Gestionnaire de symboles"
  - "Gestionnaire de symboles, interfaces"
  - "Gestionnaire de symboles, évaluer les variables"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Interfaces de fournisseur de symboles
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Voici les interfaces de gestion de symboles pour [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Discussion  
 Ces interfaces sont utilisées pour évaluer les variables dans une pile des appels en mode arrêt.  Elles sont implémentées uniquement pour les fournisseurs de symbole du common langage \(SP\) runtime.  
  
|Interface|implémenté par|Description|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|représente l'adresse d'un élément.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Représente l'adresse d'un élément, qui donne accès à l'identificateur de processus|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Représente un symbole ou un type de tableau de tableau.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|représente un symbole de classe ou un type de classe.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Représente un fournisseur de symbole COM\+ avec les méthodes qui sont spécifiques au code managé.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Représente un fournisseur de symbole COM\+ avec les méthodes qui sont spécifiques au code managé et étend **l'IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|représente un symbole ou un type qui sont un conteneur pour d'autres symboles ou types.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Représente un attribut personnalisé qui peut être attaché à un symbole.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|représente une requête pour des attributs personnalisés sur une méthode ou un type.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|permet d'accéder aux attributs personnalisés sur un symbole.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|L'interface de base pour tout type qui peut être déterminée au moment de l'exécution.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|représente un champ dynamique pour un objet d' [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|représente un type énumération.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Étend les types de champs disponibles pour prendre en charge les génériques de code managé.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|la classe de base pour tous les champs ; représente une description d'un symbole ou d'un type.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|représente la définition d'un champ pour un type générique de code managé.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|représente une instance d'un champ pour un type générique de code managé.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|représente un paramètre pour un type générique de code managé.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|représente une méthode.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|représente un modificateur facultatif de débogage.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|représente un pointeur.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|représente une valeur d'énumération de type primitif d'une interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Représente une propriété d'une classe à partir de le code managé qui peut être get ou défini.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Représente un fournisseur de symboles qui fournit des symboles et des types.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Représente un fournisseur de symbole avec un accès direct aux métadonnées et vide des interfaces de symbole.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|représente la capacité de créer un champ qui représente un type.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|étend l' **IDebugTypeFieldBuilder** pour pouvoir créer des types de tableau.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Représente une collection d'objets [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md).|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Représente une collection d'objets [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Représente une collection d'objets [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).|  
  
## Voir aussi  
 [Référence API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)