---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty (méthode), IActiveScriptProperty (interface)"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
Définit la propriété qui est spécifiée par le paramètre.  
  
## Syntaxe  
  
```  
HRESULT SetProperty(  
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
 Valeur de propriété à définir.  
  
 `pvarIndex`  
 Non utilisé.  
  
 `pvarValue`  
 Valeur de la propriété.  
  
 Les valeurs autorisées pour `dwProperty` sont décrites dans le tableau suivant.  
  
|Constante|Valeur|Signification|  
|---------------|------------|-------------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Force le moteur de script pour se diviser en mode entier au lieu du mode de virgule flottante.  La valeur par défaut est `False`.|  
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
 Pour activer ou désactiver la division d'entier, appelez `SetProperty` et convertissez `Boolean` à `Object`.  Par défaut, la valeur de propriété est `False`.  Si vous lui affectez à `True`, les opérations de division retournent uniquement les entiers.  
  
 Pour activer ou désactiver la comparaison de chaînes personnalisée, `SetProperty` appeler et passer une valeur d' `Object` .  L'objet que vous passez dans doit implémenter l'interface [IActiveScriptStringCompare, interface](../../winscript/reference/iactivescriptstringcompare-interface.md).  La méthode de [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) d'interface d' [IActiveScriptStringCompare, interface](../../winscript/reference/iactivescriptstringcompare-interface.md) est appelée chaque fois qu'une chaîne comparent la fonction est exécutée.  
  
 Pour sélectionner l'ensemble de fonctionnalités de langage à prendre en charge lorsque le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est initialisé, appelez `SetProperty` et passez une valeur qui correspond au jeu de fonctionnalités de langage à activer pour SCRIPTPROP\_INVOKEVERSIONING.  Si cette propriété a la valeur 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), les fonctionnalités de langue disponibles sont les mêmes que celles qui sont apparus dans la version 5,7 du moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  S'il a la valeur 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), les fonctionnalités de langue disponibles sont celles qui sont apparues dans la version 5,7 en plus de les nouvelles fonctionnalités ajoutées dans la version 5,8.  Par défaut, cette propriété a la valeur 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), qui est l'équivalent de la fonctionnalité de langage définie qui s'est affichée dans la version 5,7, à moins que l'hôte prend en charge le comportement par défaut différent.  Par exemple, Internet Explorer 8 sélectionne dans les fonctionnalités de langage d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] prises en charge par le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de la version 5,8 par défaut lorsque le mode de document par défaut pour Internet Explorer 8 est état « de normes d'Internet Explorer 8 ».  Basculer le mode Document d'Internet Explorer 8 vers le mode de normes ou de caprices Internet Explorer 7 réinitialise le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] pour prendre en charge la fonctionnalité de langage définie qui existait dans le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de la version 5,7.  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING doit être défini uniquement lorsque le moteur de script d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est initialisé.  
  
## Exemple  
 L'exemple suivant montre comment forcer le moteur de script pour utiliser la division d'entier et comment permettre la surcharge de la fonction de comparaison.  
  
```csharp  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## Voir aussi  
 [définir la compatibilité des documents](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informations sur la version](../../javascript/reference/javascript-version-information.md)