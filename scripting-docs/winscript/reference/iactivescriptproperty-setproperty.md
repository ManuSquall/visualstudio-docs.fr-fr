---
title: 'IActiveScriptProperty :: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571306"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Définit la propriété spécifiée par le paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
 Les valeurs autorisées pour `dwProperty` sont décrites dans le tableau suivant.  
  
|Constante|valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Force le moteur de script à diviser en mode entier au lieu du mode à virgule flottante. La valeur par défaut est `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permet de remplacer la fonction de comparaison de chaînes du moteur de script.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informe le moteur de script qu’aucun autre moteur de script n’existe pour contribuer à l’objet global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Force le moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] à sélectionner un ensemble de fonctionnalités de langage à prendre en charge. L’ensemble par défaut des fonctionnalités de langage prises en charge par le moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est équivalent à l’ensemble de fonctionnalités de langage qui apparaissait dans la version 5,7 du moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_INVALIDARG`|Un argument n’est pas valide.|  
|`E_UNEXPECTED`|L’appel n’était pas attendu (par exemple, le moteur de script n’a pas encore été chargé ou initialisé).|  
  
## <a name="remarks"></a>Notes  
 Pour activer ou désactiver la Division d’entiers, appelez `SetProperty` et convertissez un `Boolean` en `Object`. Par défaut, la valeur de la propriété est `False`. Si vous lui affectez la valeur `True`, les opérations de division ne retournent que des entiers.  
  
 Pour activer ou désactiver la comparaison de chaînes personnalisée, appelez `SetProperty` et transmettez une valeur `Object`. L’objet que vous transmettez doit implémenter l' [interface IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)de l’interface. La méthode [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) de l’interface d' [interface IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) est appelée chaque fois qu’une fonction de comparaison de chaînes est exécutée.  
  
 Pour sélectionner l’ensemble de fonctionnalités de langage à prendre en charge lors de l’initialisation du moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], appelez `SetProperty` et transmettez une valeur qui correspond au jeu de fonctionnalités de langage à activer pour SCRIPTPROP_INVOKEVERSIONING. Si cette propriété a la valeur 1 (SCRIPTLANGUAGEVERSION_5_7), les fonctionnalités de langage disponibles sont les mêmes que celles apparues dans la version 5,7 du moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. S’il est défini sur 2 (SCRIPTLANGUAGEVERSION_5_8), les fonctionnalités de langage disponibles sont celles qui sont apparues dans la version 5,7 en plus des nouvelles fonctionnalités qui ont été ajoutées dans la version 5,8. Par défaut, cette propriété a la valeur 0 (SCRIPTLANGUAGEVERSION_DEFAULT), qui est équivalente à l’ensemble de fonctionnalités de langage apparaissant dans la version 5,7, sauf si l’hôte prend en charge un comportement par défaut différent. Par exemple, Internet Explorer 8 choisit les fonctionnalités de langage [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui sont prises en charge par la version 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script par défaut lorsque le mode de document par défaut pour Internet Explorer 8 est le mode « Internet Explorer 8 standard ». Le passage du mode de document Internet Explorer 8 à la version standard d’Internet Explorer 7 ou au mode Quirks réinitialise le moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] pour prendre en charge uniquement le jeu de fonctionnalités de langage qui existait dans la version 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING doit être défini uniquement lorsque le moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est en cours d’initialisation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment forcer le moteur de script à utiliser la Division d’entiers et comment autoriser la surcharge de la fonction de comparaison.  
  
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
 [Définition](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85)) de la compatibilité des documents    
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)    
 [Informations de version](../../javascript/reference/javascript-version-information.md)