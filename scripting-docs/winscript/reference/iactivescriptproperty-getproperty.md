---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e68cb73b1b94b84d5133e1c7489bc8bf6309aea
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091297"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtient la propriété qui est spécifiée par le paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
|Constante|Value|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Force le moteur de script pour diviser en mode entier plutôt qu’en mode de point flottant.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permet à la fonction de comparaison de chaîne du moteur de script à remplacer.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informe le moteur de script sans les autres moteurs de script existent pour contribuer à l’objet global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Force le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script pour sélectionner un ensemble de fonctionnalités de langage pris en charge. L’ensemble par défaut de fonctionnalités de langage pris en charge par le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script est équivalent à l’ensemble de fonctionnalités de langage qui s’est affiché dans la version 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n'a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Notes  
 L’hôte peut utiliser la propriété SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION pour informer un moteur de script sans les autres moteurs de script existent pour contribuer à l’objet global. Par exemple, Internet Explorer peut informer le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur contenant la page restituée seulement [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripts. Par conséquent, seuls les [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur peut ajouter de nouvelles propriétés à la fenêtre de l’objet global, et il n’existe aucun moteur Visual Basic Scripting Edition (VBScript) pour faire de même. Le moteur peut ignorer cet indicateur ou pouvez l’utiliser pour optimiser la gestion des nouveaux membres qui sont ajoutés à l’objet global.  
  
 L’hôte peut utiliser la propriété SCRIPTPROP_INVOKEVERSIONING pour sélectionner le jeu de fonctionnalités de langage pour être pris en charge lorsque le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script est démarré. Si cette propriété est définie sur 1 (SCRIPTLANGUAGEVERSION_5_7), les fonctionnalités de langage disponibles sont les mêmes que celles qui s’est affiché dans la version 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script. Si elle est définie sur 2 (SCRIPTLANGUAGEVERSION_5_8), les fonctionnalités de langage disponibles sont ceux qui s’est affiché dans la version 5.7, en plus des fonctionnalités qui ont été ajoutées dans la version 5.8. Par défaut, cette propriété est définie sur 0 (SCRIPTLANGUAGEVERSION_DEFAULT), ce qui équivaut à l’ensemble de fonctionnalités de langage qui s’est affiché dans la version 5.7, sauf si l’hôte prend en charge un comportement par défaut différente. Par exemple, Internet Explorer 8 accepte le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] les fonctionnalités de langage prises en charge par la version 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script par défaut lorsque le mode de document pour Internet Explorer 8 est en mode « Normes Internet Explorer 8 ».  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de la compatibilité de Document](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informations de version](../../javascript/reference/javascript-version-information.md)