---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571418"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtient la propriété spécifiée par le paramètre.  
  
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
 Valeur de la propriété à récupérer.  
  
 `pvarIndex`  
 Non utilisé.  
  
 `pvarValue`  
 Valeur de la propriété.  
  
 Les valeurs autorisées pour `dwProperty` sont décrites dans le tableau suivant.  
  
|Constante|Valeur|Signification|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Force le moteur de script à diviser en mode entier au lieu du mode à virgule flottante.|  
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
 L’hôte peut utiliser la propriété SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION pour informer un moteur de script qu’aucun autre moteur de script n’existe pour contribuer à l’objet global. Par exemple, Internet Explorer peut informer le moteur de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que la page rendue contient uniquement des scripts [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Ainsi, seul le moteur de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] peut ajouter de nouvelles propriétés à la fenêtre d’objets globale, et il n’existe aucun moteur d’Visual Basic Scripting Edition (VBScript) pour faire de même. Le moteur peut ignorer cet indicateur ou peut l’utiliser pour optimiser la gestion des nouveaux membres qui sont ajoutés à l’objet global.  
  
 L’hôte peut utiliser la propriété SCRIPTPROP_INVOKEVERSIONING pour sélectionner l’ensemble de fonctionnalités de langage à prendre en charge lors du démarrage du moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Si cette propriété a la valeur 1 (SCRIPTLANGUAGEVERSION_5_7), les fonctionnalités de langage disponibles sont les mêmes que celles apparues dans la version 5,7 du moteur de script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. S’il est défini sur 2 (SCRIPTLANGUAGEVERSION_5_8), les fonctionnalités de langage disponibles sont celles qui sont apparues dans la version 5,7 en plus des fonctionnalités qui ont été ajoutées dans la version 5,8. Par défaut, cette propriété a la valeur 0 (SCRIPTLANGUAGEVERSION_DEFAULT), qui est équivalente à l’ensemble de fonctionnalités de langage apparaissant dans la version 5,7, à moins que l’hôte ne prenne en charge un comportement par défaut différent. Par exemple, Internet Explorer 8 s’intègre aux fonctionnalités de langage de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] prises en charge par la version 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur de script par défaut lorsque le mode de document pour Internet Explorer 8 est le mode « Internet Explorer 8 standard ».  
  
## <a name="see-also"></a>Voir aussi  
 [Définition](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85)) de la compatibilité des documents   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informations de version](../../javascript/reference/javascript-version-information.md)