---
title: IActiveScriptProperty::SetProperty | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Définit la propriété qui est spécifiée par le paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `dwProperty`  
 Valeur de propriété à définir.  
  
 `pvarIndex`  
 Non utilisé.  
  
 `pvarValue`  
 Valeur de la propriété.  
  
 Les valeurs autorisées pour `dwProperty` sont décrits dans le tableau suivant.  
  
|Constante|Valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Force le moteur de script pour diviser en mode entier plutôt qu’en mode de point flottant. La valeur par défaut est `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permet à la fonction de comparaison de chaîne du moteur de script doit être remplacée.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informe le moteur de script sans les autres moteurs de script existant pour contribuer à l’objet global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Force le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] le moteur de script pour sélectionner un ensemble de fonctionnalités de langage pris en charge. Ensemble de fonctionnalités de langage pris en charge par le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script est équivalent à l’ensemble de fonctionnalités de langage qui est apparue dans la version 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Remarques  
 Pour activer ou désactiver la division d’entier, appelez `SetProperty` et convertir un `Boolean` à un `Object`. Par défaut, la valeur de propriété est `False`. Si vous la définissez sur `True`, opérations de division retourne uniquement des entiers.  
  
 Pour activer ou désactiver la comparaison de chaîne personnalisée, appelez `SetProperty` et passez une `Object` valeur. L’objet que vous passez doit implémenter l’interface [IActiveScriptStringCompare (Interface)](../../winscript/reference/iactivescriptstringcompare-interface.md). Le [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) méthode de la [IActiveScriptStringCompare (Interface)](../../winscript/reference/iactivescriptstringcompare-interface.md) interface est appelée chaque fois qu’une fonction de comparaison de chaîne est exécutée.  
  
 Pour sélectionner l’ensemble des fonctionnalités de langage pris en charge lorsque le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script est initialisé, appelez `SetProperty` et passer une valeur qui correspond à la fonctionnalité de langage définie doit être activé pour SCRIPTPROP_INVOKEVERSIONING. Si cette propriété est définie sur 1 (SCRIPTLANGUAGEVERSION_5_7), les fonctionnalités de langage disponibles sont les mêmes que celles qui apparaissent dans la version 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script. Si elle est définie à 2 (SCRIPTLANGUAGEVERSION_5_8), les fonctionnalités de langage disponibles sont celles qui apparaissent dans la version 5.7 en plus des nouvelles fonctionnalités qui ont été ajoutées dans la version 5.8. Par défaut, cette propriété est définie sur 0 (SCRIPTLANGUAGEVERSION_DEFAULT), ce qui équivaut à l’ensemble de fonctionnalités de langage qui est apparue dans la version 5.7, sauf si l’hôte prend en charge un comportement différent par défaut. Par exemple, Internet Explorer 8 opts dans le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des fonctionnalités de langage qui sont pris en charge par la version 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script par défaut lorsque le mode de document par défaut pour Internet Explorer 8 est en mode « Standard d’Internet Explorer 8 ». Basculer le mode de document Internet Explorer 8 à standard d’Internet Explorer 7 ou le mode Quirks réinitialise le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] le moteur de script pour prendre en charge uniquement l’ensemble de fonctionnalités de langage qui existaient dans la version 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING doit être définie uniquement lorsque le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’initialisation du moteur de script.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment forcer le moteur de script à utiliser la division d’entier et permettre la surcharge de la fonction de comparaison.  
  
```c#  
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
  
## <a name="see-also"></a>Voir aussi  
 [Définition de la compatibilité du Document](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informations de version](../../javascript/reference/javascript-version-information.md)