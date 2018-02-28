---
title: IActiveScriptProperty::GetProperty | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtient la propriété qui est spécifiée par le paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `dwProperty`  
 La valeur de propriété à obtenir.  
  
 `pvarIndex`  
 Non utilisé.  
  
 `pvarValue`  
 Valeur de la propriété.  
  
 Les valeurs autorisées pour `dwProperty` sont décrits dans le tableau suivant.  
  
|Constante|Valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Force le moteur de script pour diviser en mode entier plutôt qu’en mode de point flottant.|  
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
 L’hôte peut utiliser la propriété SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION pour informer un moteur de script sans les autres moteurs de script existant pour contribuer à l’objet global. Par exemple, Internet Explorer peut informer le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur contenant la page restituée uniquement [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des scripts. Par conséquent, seuls les [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur peut ajouter de nouvelles propriétés à la fenêtre de l’objet global, et il n’existe aucun moteur Visual Basic Scripting Edition (VBScript) pour faire de même. Le moteur peut ignorer cet indicateur ou pouvez l’utiliser pour optimiser la gestion des nouveaux membres sont ajoutés à l’objet global.  
  
 L’hôte peut utiliser la propriété SCRIPTPROP_INVOKEVERSIONING pour sélectionner l’ensemble des fonctionnalités de langage pour être pris en charge lorsque le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script est démarré. Si cette propriété est définie sur 1 (SCRIPTLANGUAGEVERSION_5_7), les fonctionnalités de langage disponibles sont les mêmes que celles qui apparaissent dans la version 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script. Si elle est définie à 2 (SCRIPTLANGUAGEVERSION_5_8), les fonctionnalités de langage disponibles sont celles qui apparaissent dans la version 5.7 en plus des fonctionnalités qui ont été ajoutées dans la version 5.8. Par défaut, cette propriété est définie sur 0 (SCRIPTLANGUAGEVERSION_DEFAULT), ce qui équivaut à l’ensemble de fonctionnalités de langage qui est apparue dans la version 5.7, sauf si l’hôte prend en charge un comportement différent par défaut. Par exemple, Internet Explorer 8 opts dans le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] les fonctionnalités de langage pris en charge par la version 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] du moteur de script par défaut lorsque le mode de document Internet Explorer 8 est en mode « Standard d’Internet Explorer 8 ».  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de la compatibilité du Document](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informations de version](../../javascript/reference/javascript-version-information.md)