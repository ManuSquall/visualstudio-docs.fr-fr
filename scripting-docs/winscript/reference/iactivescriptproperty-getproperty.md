---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty (méthode), IActiveScriptProperty (interface)"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
Obtient la propriété spécifiée par le paramètre.  
  
## Syntaxe  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### Paramètres  
 `dwProperty`  
 La valeur de propriété à obtenir.  
  
 `pvarIndex`  
 Non utilisé.  
  
 `pvarValue`  
 Valeur de la propriété.  
  
 Les valeurs autorisées pour `dwProperty` sont décrites dans le tableau suivant.  
  
|Constante|Valeur|Signification|  
|---------------|------------|-------------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Force le moteur de script pour se diviser en mode entier au lieu du mode de virgule flottante.|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|Permet la chaîne comparent la fonction du moteur de script à remplacer.|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|Informe le moteur de script qu'aucun moteur de script n'existe pas à fournir à l'objet global.|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|Force le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] pour sélectionner un ensemble de fonctionnalités de langage à prendre en charge.  L'ensemble de fonctionnalités de langage par défaut prises en charge par le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] équivaut à la fonctionnalité de langage définie qui s'est affichée dans la version 5,7 du moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .|  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'est pas valide.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
  
## Notes  
 L'hôte peut utiliser la propriété de SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION pour notifier à un moteur de script qu'aucun moteur de script n'existe pas à fournir à l'objet global.  Par exemple, Internet Explorer peut informer le moteur d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que la page affichée contient uniquement des scripts de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Par conséquent, seul le moteur d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] peut ajouter de nouvelles propriétés dans la fenêtre globale d'objet, et il n'existe aucune moteur de Visual Basic Scripting Edition \(VBScript\) pour effectuer la même opération.  Le moteur peut ignorer cette balise ou peut l'utiliser pour optimiser la gestion des nouveaux membres qui sont ajoutés à l'objet global.  
  
 L'hôte peut utiliser la propriété de SCRIPTPROP\_INVOKEVERSIONING pour sélectionner l'ensemble de fonctionnalités de langage à prendre en charge lorsque le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est démarré.  Si cette propriété a la valeur 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), les fonctionnalités de langue disponibles sont les mêmes que celles qui sont apparus dans la version 5,7 du moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  S'il a la valeur 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), les fonctionnalités de langue disponibles sont celles qui sont apparues dans la version 5,7 en plus de les fonctionnalités ajoutées dans la version 5,8.  Par défaut, cette propriété a la valeur 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), qui est l'équivalent de la fonctionnalité de langage définie qui s'est affichée dans la version 5,7, à moins que l'hôte prend en charge le comportement par défaut différent.  Par exemple, Internet Explorer 8 sélectionne dans les fonctionnalités de langage d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] prises en charge par le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de la version 5,8 par défaut lorsque l'état Document pour Internet Explorer 8 est état « de normes d'Internet Explorer 8 ».  
  
## Voir aussi  
 [définir la compatibilité des documents](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informations sur la version](../../javascript/reference/javascript-version-information.md)